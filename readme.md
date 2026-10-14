# [z] Vehicle Routing Problem (VRP) based on Simulated Annealing (SA) (Matlab Code Implementation)

​  
Use Matlab to solve VRP problem with Simulated Annealing (SA). What is the VRP problem?
Everyone should be familiar with the Traveling Salesman Problem (TSP), which is to find the shortest path for a salesman who starts from one warehouse and visits all cities along the way before returning to the warehouse. In the TSP, there is only one salesman. How can we solve the problem of multiple salesmen (vehicles) delivering goods simultaneously?
This leads to the VRP problem, which is based on the TSP problem and adds two additional constraints:
Multiple delivery vehicles are involved in the process.
The capacity of each traveler (vehicle) to carry goods.
In other words, the TSP problem is a special case of the VRP problem (without considering capacity and only one vehicle).
📚2 Running Results Editing
Editor
Part of the code:
clc;  
clear;  
close all;  
T0 = 10000000 ; % initial temperature  
r = 0.999 ; % temperature damping rate  
Ts = 0.001 ; % stop temperature  
model = initModel();  
% initialization  
while(1)  
route = randomSol(model);  
if(isFeasible(route,model))  
break;  
end  
end  
cost = calculateCost(route,model);  
T = T0;  
min = cost;  
cnt = 1;  
% SA  
while(T > Ts)  
flag = '#';  
mode = randi([1 3]);  
newRoute = createNeibor(route,model,mode);  
newCost = calculateCost(newRoute,model);  
delta = newCost - cost;  
if(delta < 0)  
cost = newCost;  
route = newRoute;  
flag = '*';  
else  
p=exp(-delta/T);  
if rand <= p  
cost = newCost;  
route = newRoute;  
flag = '^';  
end  
end  
if cost < min  
min = cost;  
end  
costArr(cnt) = cost;  
T = T*r; % annealing  
disp([flag 'Iteration ' num2str(cnt) ': Best Cost = ' num2str(cost) ' T = ' num2str(T)]);  
cnt = cnt+1;  
end  
disp(min);  
plot(costArr);  
🌈3 Matlab code implementation
🎉4 References
​  

## Images

![[z] Vehicle Routing Problem (VRP) based on Simulated Annealing (SA) (Matlab code implementation)](01.gif)
![[z] Vehicle Routing Problem (VRP) based on Simulated Annealing (SA) (Matlab code implementation)](02.png)
![[z] Vehicle Routing Problem (VRP) based on Simulated Annealing (SA) (Matlab code implementation)](03.png)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
