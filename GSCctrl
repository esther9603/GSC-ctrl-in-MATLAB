delete(GSC1)
delete(instrfindall);
delete(MCU)

%%
clc;
clear;
close all; 

%%
%%%%%%%%%%%%%%%%%%%%%%% Initialize parameter %%%%%%%%%%%%%%%%%%%%%%%
global GSC1; global start; 
global f; %flag 

Operation_Time = 15; % operating time 
start = 0;

%% 
%%%%%%%%%%%%%%%%%%%%%%% Initial setting %%%%%%%%%%%%%%%%%%%%%%%

GSC1=serialport("COM12",9600, "DataBits",8, "StopBits", 1); %set COM#, BaudRate 
configureTerminator(GSC1,"CR/LF");
GSC1.FlowControl = 'hardware';
disp('gsc1 open');
writeline(GSC1,"D:1S4000F8500R10"); %set stage velocity 
pause(5);

f = 1; 

disp('countdown 3')
pause(1);
disp('countdown 2')
pause(1);
disp('countdown 1')
pause(1);

start = 1;

while(1)
    if(start==1)
        count
         if(f==1)
            writeline(GSC1, 'M:W+P5000'); % set stage distance
            writeline(GSC1, 'G:'); % move the stage 
            f = 2; 
        elseif (f==2)
            writeline(GSC1, 'L:E'); %stop the stage instantly (for gradual stop, use L:W)
        end
        pause(0.01);
    end
end      

delete(GSC1);
