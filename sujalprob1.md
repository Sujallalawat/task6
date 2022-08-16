# CP Task#6
## Problem:-

<p>
Sujal is in LH 16 at 11:30 pm.As students are required to be present in their respective Halls by midnight,Sujal rushes towards Hall 12,his assigned hall.Sujal wants to visit his friends before reaching his hall.He has two friends,one resides in Hall 2 while the other resides in Hall 5.Due to the lack of time ,he can only visit one before time runs out.

Calculate the number of ways in which he can return to his hall as soon as possible while visiting only one of his friends.Assume the college campus to be a grid of size m*n with LH 16 located at the origin,Hall 12 located at (m,n),Hall 2 located at (x1, y1) and Hall 5 located at (x2,y2).His movements can be made only along the grid.

## Input:- 
The first line of the input contains two integers m and n.
The second line of the input contains 4 integers x1,y1,x2, y2 in the given order.

## Output:-
Display the number of ways in which Sujal can reach his destination.

Note:You have to consider the shortest path.  

## Sample Input:-
3 2  
1 1 2 2  
## Sample Output:-
4</p>

# solution:-

<p>#include<stdio.h>
int f(int n)
{
    if(n==0)
    return 1;
    else{
    int i,fa=1;
    for(i=1;i<=n;i++)
    {
        fa=fa*i;
    }
    return fa;
    }

}
int main()  
{
    int m,n,t,u,v;    
    scanf("%d %d",&m,&n);  
    int x1,y1,x2,y2;  
    scanf("%d %d %d %d",&x1,&y1,&x2,&y2);  
    if(x2>=x1 && y2>=y1)
    {
        t=(f(x1+y1)/(f(x1)*f(y1)))*(f(m+n-x1-y1)/(f(m-x1)*f(n-y1))-f(x2+y2-x1-y1)*f(m+n-x2-y2)/(f(x2-x1)*f(y2-y1)*f(m-x2)*f(n-y2)))+f(m+n-x2-y2)/(f(m-x2)*f(n-y2))*(f(x2+y2)/(f(x2)*f(y2))-f(x1+y1)/(f(x1)*f(y1))*(f(x2+y2-x1-y1)/(f(x2-x1)*f(y2-y1))));  
        printf("%d",t);  
    }
    else if(((x2>x1)&&(y2<y1)) || ((x2<x1)&&(y2>y1)))
    {
        u=f(x1+y1)/(f(x1)*f(y1))*(f(m+n-x1-y1)/(f(m-x1)*f(n-y1)))+f(x2+y2)/(f(x2)*f(y2))*(f(m+n-x2-y2)/(f(m-x2)*f(n-y2)));
        printf("%d",u);  
    }
    else if(x2<x1 && y2<y1)  
    {
        v=f(x2+y2)/(f(x2)*f(y2))*(f(m+n-x2-y2)/(f(m-x2)*f(n-y2))-(f(x1+y1-x2-y2)/(f(x1-x2)*f(y1-y2)))*f(m+n-x1-y1)/(f(m-x1)*f(n-y1)))+f(m+n-x1-y1)/(f(m-x1)*f(n-y1))*(f(x1+y1)/(f(x1)*f(y1))-(f(x2+y2)/(f(x2)*f(y2))*f(x1+y1-x2-y2)/(f(x1-x2)*f(y1-y2))));  
        printf("%d",v);    
    }  
    return 0;
}
</p>