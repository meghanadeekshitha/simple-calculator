%{
int ch = 0,i;
float a, b;
%}

dig [0-9]+|([0-9]*)"."([0-9]+)
add "+"
sub "-"
mul "*"
div "/"
pow "^"
ln \n
%%
{dig} {digi();}
{add} {ch=1;}
{sub} {ch=2;}
{mul} {ch=3;}
{div} {ch=4;}
{pow} {ch=5;}
{ln} {printf("\n The Answer :%f\n\n",a);}
%%
digi()
{
if(ch==0)

a=atof(yytext);

else
{
b=atof(yytext);

switch(ch)
{
case 1:a=a+b;
break;

case 2:a=a-b;
break;

case 3:a=a*b;
break;

case 4:a=a/b;
break;

case 5:for(i=a;b>1;b--)
a=a*i;
break;
}
ch=0;
}
}

main(int argv,char *argc[])
{
yylex();
}

yywrap()
{
return 1;
}
