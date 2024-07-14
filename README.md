package Dijkstras_algo;
import java.util.Scanner;
public class Dijkstras {
static int a[][];//declaring an array
static int n;
public static void main(String args[])
{
	Scanner in =new Scanner(System.in);//the scanner object name:in;
	System.out.println("enter the number of vertices:");
	n=in.nextInt();//by using the  created object in we are scanning <nextInt> means next integer input from the user
	System.out.println("enter the cost adjacent matrix");
	a=new int[n][n];//initialization of the array
	for(int i=0;i<n;i++)
	{
		for(int j=0;j<n;j++)
		{
			a[i][j]=in.nextInt();
		}
	}
	System.out.println("enter the source vertex");
	int s=in.nextInt();
	Dijkstras(s);
	in.close();
}
public static void Dijkstras(int s)
{
	int visited[]=new int[n];//creates and array with n elements
	int d[]=new int[n];
	int i,u,v;
	for( i=0;i<n;i++)//this loop is used for initalizing the visited and the min distance 
	{
		visited[i]=0;
		d[i]=a[s][i];
		
	}
	visited[s]=1;
	d[s]=0;//to maintain no loop thing(to avoid any loops)
	i=1;
	while(i<=n-1)
	{
		u=Extra_Min(visited,d);//it initialize the Extra_MIn method,to find the unvisited vretex and also find the min distance and to store that in the u variable
		visited[u]=1;
		i++;
		for(v=0;v<n;v++)
		{
			if(d[u]+a[u][v]<d[v]&& visited[v]==0)//comparing the already stored shortest distance (the distance to vertex v through vertex u is shorter then the currently known shortest distance)
			{
				d[v]=d[u]+a[u][v];
			}
		}
	}
		for( i=0;i<n;i++)//to print the shortest path
		{
			if(i!=s)//to check whether the current vertex is not the source vertex or not
			{
				System.out.println(s+"->"+i+":"+d[i]);//to print the shortest distance from the source to i along with d[i];
			}
		}
		
}
	
	public static  int Extra_Min (int visited[],int d[])
	{
		int i,j=0,min=999;
		//i<to loop over each vertex> j<store the index of the vertex with min distance>: min <to store the nim idstance found>
		for( i=0;i<n;i++)
		{
			if(d[i] < min && visited[i]==0)
			{
				min=d[i];
				j=i;
			}
			
		}
		return j;
	}
	


	
}







//PRIMS ALGORITHM:

package prims_algo;
import java.util.Arrays;
import java.util.Scanner;//

public class prims {
	static  int a[][];//it stores the cost matrix;
	static int n;//for number of vertices;

	public static void main(String args[]) //public: it can be called outside of the class, static:it is called without creating any instance of the class
	{
		// TODO Auto-generated method stub
		System.out.println("enter the number of vertices");
		Scanner scanner=new Scanner(System.in);
		n=scanner.nextInt();
		a=new int[n][n];
		System.out.println("enter the cost matrix");
		for(int i=0;i<n;i++)
		{
			for(int j=0;j<n;j++)
			{
				a[i][j]=scanner.nextInt();
			}
		}
		prim();
		scanner.close();
		
	}
	public static void prim()
	{
		boolean[] selected=new boolean[n];
		int no_edge=0;
		int sum=0;
		Arrays.fill(selected, false);//initialize all elements of the selected array to false
		selected[0]=true;
		System.out.println("Edge : Weight");
		while(no_edge<n-1)
		{
			int x=0,y=0,min=999;
			for(int i=0;i<n;i++)
			{
				if(selected[i]==true)//check vertices incuded in the MST;
				{
					for(int j=0;j<n;j++)
					{
						if(!selected[j] && a[i][j]!=0)
						{
							if(min > a[i][j])
							{
								min=a[i][j];
								x=i;
								y=j;
							}
						}
					}
				}
			}
			System.out.println(x+"-"+y+":"+a[x][y]);
			sum=sum+a[x][y];
			selected[y]=true;
			no_edge++;
		}
		System.out.println("Cost of Tree"+sum);
		
		
	}
	
}














