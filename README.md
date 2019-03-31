# Queen-attack-2
Code for Queen's attack Hackerrank code in c++

#include<bits/stdc++.h>

using namespace std;

int step(int k,int n,int rq,int cq,vector<vector<int>> obstacles)

{

int lu,ru,rd,ld,rs,ls,up,down;

ru=min(rq,n-cq-1);lu=min(rq,cq);rd=min(n-rq-1,n-cq-1);ld=min(n-rq-1,cq);

up=rq;down=n-rq-1;rs=n-cq-1;ls=cq;

for(int i=0;i<k;i++)

{
    //////////////////////// Diagonal 1 //////////////////////////
    
    if(obstacles[i][0]-rq+(obstacles[i][1]-cq)==0 && obstacles[i][1]>cq)
    {
        if ( abs(obstacles[i][0]-rq)-1<ru)
      {ru=abs(obstacles[i][0]-rq)-1;}
    }
     else if(obstacles[i][0]-rq+(obstacles[i][1]-cq)==0 &&  obstacles[i][1]<cq )

    {     if ( abs(obstacles[i][0]-rq)-1<ld)
            {ld=abs(obstacles[i][0]-rq)-1;}
    }
    else if(obstacles[i][0]-rq==obstacles[i][1]-cq && obstacles[i][1]>cq )
    {
    if ( abs(obstacles[i][0]-rq)-1<rd)
    {rd=abs(obstacles[i][0]-rq)-1;}
    }

     else if(obstacles[i][0]-rq==obstacles[i][1]-cq && obstacles[i][1]<cq  )
    {  if(abs(obstacles[i][0]-rq)-1<lu)
         {lu=abs(obstacles[i][0]-rq)-1;}
    }

    else if(obstacles[i][1]-cq==0 && obstacles[i][0]>rq)
    {
        if(obstacles[i][0]-rq-1<down ){down=obstacles[i][0]-rq-1;}
    }

    else if(obstacles[i][1]-cq==0 && obstacles[i][0]<rq)
    {   if(abs(obstacles[i][0]-rq)-1<up)
        {up=abs(obstacles[i][0]-rq)-1;}
    }
    else if(obstacles[i][0]-rq==0 && obstacles[i][1]-cq>0 )
    {
        if(obstacles[i][1]-cq-1<rs ){rs=obstacles[i][1]-cq-1;}
    }
     else if(obstacles[i][0]-rq==0 && obstacles[i][1]-cq<0)
    {
          if(abs(obstacles[i][1]-cq)-1<ls ){ls=abs(obstacles[i][1]-cq)-1;}
    }
 //cout<<"ru"<<ru<<" rd"<<rd<<" lu"<<lu<<" ld"<<ld<<" up"<<up<<" down"<<down<<" rs"<<rs<<" ls"<<ls<<endl;

}


int stepcount=ld+ru+rd+lu+up+down+rs+ls;

return stepcount;

}

int main()

{
    int n,rq,cq;
     int k;

cin>>n>>k>>rq>>cq;

vector<vector<int>> obstacles(k,vector<int>(2));

for(int i=0;i<k;i++)

{for(int j=0;j<2;j++)

{cin>>obstacles[i][j];
         obstacles[i][j] +=-1;
         }
 
 }
   
   cout<<step(k,n,rq-1,cq-1,obstacles);
}
