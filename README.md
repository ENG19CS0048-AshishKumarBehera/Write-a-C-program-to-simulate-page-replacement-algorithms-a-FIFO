# Write-a-C-program-to-simulate-page-replacement-algorithms-a-FIFO
Code:
#include<stdio.h>
int main()
{
 int i,j,n,a[50],frame[10],no,k,avail,count=0;
 printf("\n ENTER THE NUMBER OF PAGES:\n");
 scanf("%d",&n);
 printf("\n ENTER THE PAGE NUMBER :\n");
 for(i=1;i<=n;i++)
 scanf("%d",&a[i]);
 printf("\n ENTER THE NUMBER OF FRAMES :");
 scanf("%d",&no);
 for(i=0;i<no;i++)
 frame[i]= -1;
 j=0;
 printf("\tref string\t page frames\n");
 for(i=1;i<=n;i++)
 {
 printf("%d\t\t",a[i]);
 avail=0;
 for(k=0;k<no;k++)
 if(frame[k]==a[i])
 avail=1;
 if (avail==0)
 {
 frame[j]=a[i];
 j=(j+1)%no;
 count++;
 for(k=0;k<no;k++)
 printf("%d\t",frame[k]);
 }
 printf("\n");
 }
 printf("Page Fault Is %d",count);
 return 0;
}
b)LRU
#include<stdio.h>
int main()
{
int frames[10], temp[10], pages[10];
int total_pages, m, n, position, k, l, total_frames;
int a = 0, b = 0, page_fault = 0;
printf("\nEnter Total Number of Frames:\t");
scanf("%d", &total_frames);
for(m = 0; m < total_frames; m++)
{
frames[m] = -1;
}
printf("Enter Total Number of Pages:\t");
scanf("%d", &total_pages);
printf("Enter Values for Reference String:\n");
for(m = 0; m < total_pages; m++)
{
printf("Value No.[%d]:\t", m + 1);
scanf("%d", &pages[m]);
}
for(n = 0; n < total_pages; n++)
{
a = 0, b = 0;
for(m = 0; m < total_frames; m++)
{
if(frames[m] == pages[n])
{
a = 1;
b = 1;
break;
}}
if(a == 0)
{
for(m = 0; m < total_frames; m++)
{
if(frames[m] == -1)
{
frames[m] = pages[n];
b = 1;
page_fault++;
break;
}}}
if(b == 0)
{
for(m = 0; m < total_frames; m++)
{
temp[m] = 0;
}
for(k = n - 1, l = 1; l <= total_frames - 1; l++, k--
){
for(m = 0; m < total_frames; m++)
{
if(frames[m] == pages[k])
{
temp[m] = 1;
}}}
for(m = 0; m < total_frames; m++)
{
if(temp[m] == 0)
position = m;
}
frames[position] = pages[n];
page_fault++;
}
printf("\n");
for(m = 0; m < total_frames; m++)
{
printf("%d\t", frames[m]);
}}
printf("\nTotal Number of Page Faults:\t%d\n",
page_fault);
return 0;
}
c)LFU
#include<stdio.h>
int main()
{
int f,p;
int pages[50],frame[10],hit=0,count[50],time[50];
int i,j,page,flag,least,minTime,temp;
printf("Enter no of frames : ");
scanf("%d",&f);
printf("Enter no of pages : ");
scanf("%d",&p);
for(i=0;i<f;i++)
{
frame[i]=-1;
}
for(i=0;i<50;i++)
{
count[i]=0;
}
printf("Enter page no : \n");
for(i=0;i<p;i++)
{
scanf("%d",&pages[i]);
}
printf("\n");
for(i=0;i<p;i++)
{
count[pages[i]]++;
time[pages[i]]=i;
flag=1;
least=frame[0];
for(j=0;j<f;j++)
{
if(frame[j]==-1 || frame[j]==pages[i])
{
if(frame[j]!=-1)
{
hit++;
}
flag=0;
frame[j]=pages[i];
break;
}
if(count[least]>count[frame[j]])
{
least=frame[j];
}}
if(flag)
{
minTime=50;
for(j=0;j<f;j++)
{
if(count[frame[j]]==count[least] && time[frame[j]]<minTime)
{
temp=j;
minTime=time[frame[j]];
}}
count[frame[temp]]=0;
frame[temp]=pages[i];
}
for(j=0;j<f;j++)
{
printf("%d ",frame[j]);
}
printf("\n");
}
printf("Page hit = %d",hit);
return 0;
}
1
