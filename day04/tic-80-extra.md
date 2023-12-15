# Day 4 Extra
![A spinning grid of colours with a change centre of rotation](./day04extra.gif)

```
s=math.sin 
w=240
h=136
t=0
function TIC()
for i=0,w*h do
x=i%w
y=i//w
p=x-w/2+s(t)*w/2
q=y-h/2+s(t)*h/2
v=s(t-11)
z=s(t)
pix(x,y,((v*p-z*q)//1&(z*p+v*q)//1)/5)
end 
t=t+.02 
end
```

and a size optimised version (167 characters)

```
s=math.sin w=240h=136t=0 function TIC()for i=0,w*h do x=i%w y=i//w p=x-w/2+s(t)*w/2q=y-h/2+s(t)*h/2v=s(t-11)z=s(t)pix(x,y,((v*p-z*q)//1&(z*p+v*q)//1)/5)end t=t+.02 end
```
