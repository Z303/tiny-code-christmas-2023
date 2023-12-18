# Day 8 Extra
![Coloured dots in a circle swirling around](./day08extra.gif)

```
m=math
s=m.sin

q=34

x=0
v=0
t=0 

function TIC()
	cls()
	
	for k=0,8000 do
		i=k//200
		j=k%200
		
		o=i+v p=m.pi/117*i+x 
		
		u=s(o)+s(p)
		v=s(o-11)+s(p-11)
		
		x=u+t 
		
		pix(120+u*q,68+v*q,1+i%15+j/q)
	end 
	
	t=t+.025 
end
```

and a size optimised version (180 characters)

```
m=math s=m.sin q=34x=0v=0t=0 function TIC()cls()for k=0,8000 do i=k//200j=k%200o=i+v p=m.pi/117*i+x u=s(o)+s(p)v=s(o-11)+s(p-11)x=u+t pix(120+u*q,68+v*q,1+i%15+j/q)end t=t+.025 end
```
