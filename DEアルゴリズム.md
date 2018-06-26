# matlab
clear all

global number n
number=5;
n=10;
m=20;
F=0.5;
CR=0.5;
Gmax=500;
    
%while Gmax<=500
    tic 
    for G=1:1
        load InitialPoints_300_100_100
        x = 5*IP(1:m,1:n,5);

  for k=1:Gmax     
  if k==50
     x0=x;
  elseif k==100
     x2=x;
   elseif k==150
      x3=x;
   elseif k==200
      x4=x;
   elseif k==Gmax
       x5=x;
   end   
        
        
        
        
        
        
        for i=1:m

            A=randperm(m); % 个体?序重新随机排列
            A(A==i)=[]; % 当前个体所排位置?空（?生??中?体?当前个体不参与）
            a=A(1);
            b=A(2);
            c=A(3);
            xr1=x(a,:);
            xr2=x(b,:);
            xr3=x(c,:);
            r=rand(1,n);
            v=xr1+F*(xr2-xr3);
            u=zeros(1,n);
            
            for j=1:n
                if r(1,j)<=CR || j==n
                    u(j)=v(j);
                else 
                    u(j)=x(i,j);
                end
            end

            if  fun(u)<=fun(x(i,:))

                x(i,:)=u;

            else

                x(i,:)=x(i,:);
            end
            
        end
        
  end     
        
        
        re(G)=fun(x(i,:));
    end

    disp([mean(re),min(re),max(re),std(re)])
    toc
% Gmax=5*Gmax;
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
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
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
    
