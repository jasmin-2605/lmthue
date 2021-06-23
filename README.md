#include <stdio.h>
long long gt(int k)
{
	if(k==1) return 1;
	return k*gt(k-1);
}
void check1(int n,int k)
{
	long long x = gt(n);
	int y = gt(k);
	int z = gt(n-k);
	long long t = y*z;
	long long c = x/t;
	printf("Gia tri to hop C(k)(n) = %lld",c);
}
void check2(int n)
{
	printf("Uoc nguyen to cua n : %d =",n);
	int u=3;
	while(n % 2 == 0)
	{
		printf("2");
		if(n > 2) printf("*");
		n/=2;
	}
	while(n > u)
	{
		if(n % u == 0)
		{
			while(n % u == 0)
			{
				printf("%d",u);
				if(n > u) printf("*");
				n/=u;
			}
		} else u+=2;
	}
	printf(".");
}
void check3(int n,int m)
{
	printf("Doi co so n o he 10 sang he %d : ",m);
	int a[10000];
	int x=0;
	while(n!=0)
	{
		a[x++]=n%m;
		n/=m;
	}
	for(int i=x-1;i>=0;i--)
	{
		printf("%d",a[i]);
	}
}
int main ()
{
	int n,k,m,kt=1,choose,conti;
	printf(" Nhap cac so nguyen n,k,m (n>0, 0<=k<=n , 2<=m<=10) : ");
	scanf("%d%d%d",&n,&k,&m);
	while(kt==1)
	{
		if(n < 0 || k < 0 || k > n || m < 2 || m >10)
		{
		printf("\nYeu cau nhap dung dieu kien\nNhap cac so nguyen n,k,m (n>0, 0<=k<=n , 2<=m<=10) : ");
		scanf("%d%d%d",&n,&k,&m);
		} else kt=0;
	}
	do
	{
		printf("___________Menu thuc hien cac cong viec___________\n\n");
		printf("______________Chon cac lenh sau day_______________\n\n");
		printf("1. Tinh to hop cua C(k)(n)\n");
		printf("2. Phan tich n thanh thua so nguyen to\n");
		printf("3. Doi co so n tu he 10 sang he m\n\n");
		scanf("%d",&choose);
		switch (choose)
		{
			case 1:
				check1(n,k);
				break;
			case 2:
				check2(n);
				break;
			case 3:
				check3(n,m);
				break;
			default:
				printf("Khong Ton Tai");
		}
			printf("\n\nTiep tuc dung chuc nang khac : chon '1' \nKet thuc chuong trinh : chon '0'\n");
			scanf("%d",&conti);
			printf("\n");
		} while (conti==1);
}









bai tiep:




#include <stdio.h>
#include <math.h>
int gt[11];
void output(int a[],int n)
{
	printf("\n=> Day so vua nhap : ");
	for(int i=0;i<n;i++)
	{
		printf("%d ",a[i]);
	}
}

void importArr(int a[],int n)
{
	for(int i=0;i<n;i++)
	{
		printf("Nhap gia tri mang a[%d] : ",i+1);
		scanf("%d",&a[i]);
	}
	output(a,n);
}
int ucln(int a,int b)
{
	while(a != b)
	{
		if(a > b) a-=b;
		else b-=a;
	}
	if(a==1) return 1;
	return 0;
}

void check1(int a[],int n)
{
	printf("Cap so nguyen to cung nhau : ");
	int count=0;
	for(int i=0;i<n-1;i++)
	{
		if(ucln(a[i],a[i+1])==1) printf("(%d,%d)  ",a[i],a[i+1]);
		else count++;
	}
	if(count==n-1) printf("Khong Ton Tai");
}
int kt1(int n)
{
	if(n==0 || n== 1 || n==2) return 0;
	else
	if(n > 2)
	{
		int k=sqrt(n);
		if(k*k==n) return 1;
	}
	return 0;
}
void check2(int a[],int n)
{
	printf("Cac so chinh phuong trong day : ");
	int count=0;
	for(int i=0;i<n;i++)
	{
		if(kt1(a[i])==1) printf("%d ",a[i]);
		else count++;
	}
	if(count==n-1) printf("Khong Ton Tai");
}
int kt2(int n)
{
	for(int i=1;i<=10;i++)
	{
		if(n==gt[i]) return 1;
	}
	return 0;
}
void check3(int a[],int n)
{
	printf("Cac so la giai thua va vi tri cua chinh no :\n");
	int count=0;
	for(int i=0;i<n;i++)
	{
		if(kt2(a[i])==1) printf("%d : Vi tri %d\n",a[i],i+1);
		else count++;
	}
	if(count==n) printf("Khong Ton Tai");
}
int main ()
{
	for(int i=1;i<=10;i++)
	{
		int p=1;
		for(int j=1;j<=i;j++)
		{
			p*=j;
		}
		gt[i]=p;
	}
	int choose,conti,n,a[1000];
		printf(" \nNhap gia tri n > 0 : ");
		scanf("%d",&n);
		while(n < 0)
		{
			
			printf("Yeu cau nhap n > 0.\n");
			printf("Nhap gia tri n > 0 : ");
			scanf("%d",&n);
			
		}
		importArr(a,n);
			printf("\n\n");
		do
		{
			printf("___________Menu thuc hien cac cong viec___________\n\n");
			printf("______________Chon cac lenh sau day_______________\n\n");
			printf("1. Tim cac cap so nguyen to cung nhau lien ke nhau\n");
			printf("2. Tim cac so chinh phuong\n");
			printf("3. Tim so la giai thua co so tu nhien va vi tri tuong ung cua no\n\n");
			scanf("%d",&choose);
			switch (choose)
			{
				case 1:
					check1(a,n);
					break;
				case 2:
					check2(a,n);
					break;
				case 3:
					check3(a,n);
					break;
				default:
					printf("Khong Ton Tai");
			}
			printf("\n\nTiep tuc dung chuc nang khac : chon '1' \nKet thuc chuong trinh : chon '0'\n");
			scanf("%d",&conti);
			printf("\n");
		} while (conti==1);

}

