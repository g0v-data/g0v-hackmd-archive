#0408Malab課堂
%%
n=0;
sum_x=0;
x=input('Enter a number:');
while x>=0
    sum_x=sum_x+x;
    n=n+1;
    x=input('Enter the next number:');
end
avg=sum_x/n;
fprintf('avg:%f data:%d \n',avg,n);
%%
total=1;
for ii=1:10;
    total=total*ii;
end
fprintf('total: %d\n',total);
%%
data_total=input('please number of point:');
sum_x=0;
for ii=1:data_total
    x=input('please input number:');
    sum_x=sum_x+x;
end
avg=sum_x/data_total;
fprintf('avg:%f number of point:%d \n',avg,data_total);
%%
data_total=input('please number of point:');
sum_x=0;
for ii=1:data_total
    if ii==3
        break;
    end
    x=input('please input number:');
    sum_x=sum_x+x;
end
avg=sum_x/data_total;
fprintf('avg:%f number of point:%d \n',avg,data_total);