# matlab
  x1=linspace(-5, 5, 80); 
            y1=linspace(-5, 5, 80);   
            [xx yy]=meshgrid(x1,y1);
            %zz=xx.^2+yy.^2;
            %zz=100*(xx.^2-yy)^2+(1-xx)^2;
           %zz = xx.^4-16*xx.^2+5*xx+yy.^4-16*yy.^2+5*yy;
           %zz=xx.^2-10*cos(2*pi*xx)+10+yy.^2-10*cos(2*pi*yy)+10;
           % zz=xx.^2+(xx+yy).^2;
           
            
              
            figure(1)
            contour(xx,yy,zz,35)
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            figure(2)
            surf(xx,yy,zz)
            set(gca,'FontName','Times New Roman','FontSize',20);
            xlabel('$x_1$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            ylabel('$x_2$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
            zlabel('$f(x_1,x_2)$','FontName','Times New Roman','FontSize',20,'interpreter','latex');
