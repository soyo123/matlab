# matlab
clear all

global number n

number=5;
m=30;
n=2;
c1=2;
c2=2;
w=0.4;
Tmax=100;

% while Tmax<=500
  tic  
for t=1:1
    
load InitialPoints_300_100_100
x = 5*IP(1:m,1:n,5);
v = IP(1:m,1:n,5);
pbest=x;

for i=1:m
    fx(i)=fun(pbest(i,:));
end

[A,B]=min(fx);
gbest=pbest(B,:);

for k=1:Tmax
    
    if k==1
        x0=x;
    elseif k==10
        x2=x;
    elseif k==20
        x3=x;
    elseif k==30
        x4=x;
    elseif k==Tmax
        x5=x;
    end
    
for i=1:m
    for j=1:n
        v(i,j)=w*v(i,j)+c1*rand*(pbest(i,j)-x(i,j))+c2*rand*(gbest(j)-x(i,j));
        x(i,j)=x(i,j)+v(i,j);
    end
end


for i=1:m
    if fun(x(i,:))<fun(pbest(i,:))
       pbest(i,:)=x(i,:);
    else
       pbest(i,:)=pbest(i,:);
    end
end

for i=1:m
    fx(i)=fun(pbest(i,:));   
end
    
[A,B]=min(fx);
gbest=pbest(B,:);

end

    re(t)=fun(gbest);

end

[mean(re),min(re),max(re),std(re)]
toc
% Tmax=Tmax*5;
% end

            x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
            %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy).^2+(1-xx).^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
            zz=xx.^2+(xx+yy).^2;
           
            
              
            figure(1)
            contour(xx,yy,zz,25)
            hold  on
           plot(x0(:,1),x0(:,2),'o')
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            axis([-5 5 -5 5])
            
            
            figure(2)
            x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
           %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy).^2+(1-xx).^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
           zz=xx.^2+(xx+yy).^2;
            contour(xx,yy,zz,25)
            hold  on
             plot(x2(:,1),x2(:,2),'o')
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            axis([-5 5 -5 5])
%             set (gcf,'Position',[400,100,250,250]);
%             set(gca,'LooseInset',get(gca,'TightInset'));
%             axis equal;
%             axis auto;

            
            
            
            
            figure(3)
            x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
            %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy).^2+(1-xx).^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
            zz=xx.^2+(xx+yy).^2;
            contour(xx,yy,zz,25)
            hold  on
            plot(x3(:,1),x3(:,2),'o')
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            axis([-5 5 -5 5])
            
            figure(4)
            x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
            %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy).^2+(1-xx).^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
           zz=xx.^2+(xx+yy).^2;
            contour(xx,yy,zz,25)
            hold  on
            plot(x4(:,1),x4(:,2),'o')
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            axis([-5 5 -5 5])
            
            
            figure(5)
            x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
            %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy).^2+(1-xx).^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
          % zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
            zz=xx.^2+(xx+yy).^2;
            contour(xx,yy,zz,25)
            hold  on
            scatter(x5(:,1),x5(:,2),[],'k');
            set(gca,'FontName','Times New Roman','FontSize',12);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
               axis([-5 5 -5 5])

%             set (gcf,'Position',[400,100,250,250]);
%             set(gca,'LooseInset',get(gca,'TightInset'));
%             axis equal;
%             axis auto;
% 



