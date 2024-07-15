A = [14.4,7.2,27.5,33.8,38,15.9,4.9] 
B = [54,64,44,32,37,68,62] 
[RHO,PVAL]=corr(A',B','type','Spearman') 
scatter(A,B)



x= [1 2 3 4 5] 
y = [2 5 3 8 7] 
polyfit(x,y,1) %regression line y in term of x
polyfit(y,x,1) %regression line x in term of y

x=[1 2 3 4 5 6 7] 
y=[9 8 10 12 11 13 14] 
%coefficient of correlation
r=corrcoef(x,y) 
%equation of the lines of regression
k=polyfit(x,y,1) 
h=polyfit(y,x,1) 
a=k(1) 
b=k(2) 
fprintf('the regression line y interm of x is Y=%f*x+%f',a,b) 
c=h(1) 
d=h(2) 
fprintf('the regression line x interm of y is X=%f*y+%f',c,d) 
scatter(x,y)


//curve fitting
A = [14.4,7.2,27.5,33.8,38,15.9,4.9] 
B = [54,64,44,32,37,68,62]
[RHO,PVAL]=corr(A',B','type','Spearman') 
scatter(A,B) 
x= [1 2 3 4 5] 
y = [2 5 3 8 7] 
polyfit(x,y,1) %regression line y in term of x
polyfit(y,x,1) %regression line x in term of y

X = [0 1 2 3 4] 
Y = [1 1.8 1.3 2.5 2.3] 
scatter(X,Y) 


clc 
clear 
x=[5 10 15 20 25] 
y=[16 19 23 26 30] 
n = length(x) 
syms a b 
eq1=a*sum(x)+n*b==sum(y) 
eq2=a*sum(x.*x)+b*sum(x)==sum(x.*y) 
[A,B]= equationsToMatrix([eq1 eq2],[a,b]) 
X=linsolve(A,B) 
a=double(X(1)) 
b=double(X(2)) 
fprintf('the curve fitting is given by Y=%f*x+%f',a,b)

clc 
clear 
x=[1 2 3 4 5] 
y=[0.5 2 4.5 8 12.5] 
n = length(x) 
X=log(x); 
Y=log(y); 
syms a1 b1 
eq1=n*a1+b1*sum(X)==sum(Y) 
eq2=a1*sum(X)+b1*sum(X.*X)==sum(X.*Y) 
[A,B]= equationsToMatrix([eq1 eq2],[a1,b1]) 
X=linsolve(A,B) 
a1=double(X(1)) 
b1=double(X(2)) 
a=exp(a1) 
b= b1 
fprintf('the curve fitting is given by Y=%f*x^(%f)',a,b) 

