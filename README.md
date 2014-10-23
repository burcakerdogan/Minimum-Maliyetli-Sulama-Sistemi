Minimum-Maliyetli-Sulama-Sistemi
================================

Büyük bir arazi içerisinde bulunan tarlaların sulanmasında kullanılacak sulama kanallarının minimum maliyetinin hesaplanması.
================================

 
 #include<stdio.h>
 #include<conio.h>
 #include<stdlib.h>
 #include<time.h>
 /*-lbgi
 -lgdi32
 -lcomdlg32
 -luuid
 -loleaut32
 -lole32 */

#include<graphics.h>

int dizix[50],diziy[50];
 int harita()
    {
          
    dizix[0]=50;     diziy[0]=50;
    dizix[1]=150;     diziy[1]=75;
    dizix[2]=250;    diziy[2]=120;
    dizix[3]=350;    diziy[3]=50;
    dizix[4]=450;    diziy[4]=270;
    dizix[5]=550;    diziy[5]=130;
    dizix[6]=650;    diziy[6]=50;
    dizix[7]=750;    diziy[7]=75;
    dizix[8]=50;    diziy[8]=125;
    dizix[9]=150;     diziy[9]=150;
    dizix[10]=250;    diziy[10]=175;
    dizix[11]=350;    diziy[11]=125;
    dizix[12]=450;    diziy[12]=150;
    dizix[13]=550;    diziy[13]=175;
    dizix[14]=650;    diziy[14]=125;
    dizix[15]=750;    diziy[15]=150;
    dizix[16]=50;    diziy[16]=250;
    dizix[17]=150;    diziy[17]=300;
    dizix[18]=250;    diziy[18]=250;
    dizix[19]=350;    diziy[19]=300;
    dizix[20]=450;    diziy[20]=250;
    dizix[21]=550;    diziy[21]=300;
    dizix[22]=650;    diziy[22]=250;
    dizix[23]=750;    diziy[23]=300;
    dizix[24]=50;    diziy[24]=350;
    dizix[25]=150;    diziy[25]=400;
    dizix[26]=250;    diziy[26]=350;
    dizix[27]=300;    diziy[27]=400;
    dizix[28]=450;    diziy[28]=350;
    dizix[29]=550;    diziy[29]=400;
    dizix[30]=650;    diziy[30]=350;
    dizix[31]=750;    diziy[31]=400;
    dizix[32]=50;     diziy[32]=450;
    dizix[33]=150;    diziy[33]=500;
    dizix[34]=250;    diziy[34]=450;
    dizix[35]=350;    diziy[35]=500;
    dizix[36]=450;    diziy[36]=450;
    dizix[37]=550;    diziy[37]=500;
    dizix[38]=650;    diziy[38]=450;
    dizix[39]=750;    diziy[39]=500;
    dizix[40]=50;     diziy[40]=550;
    dizix[41]=150;    diziy[41]=600;
    dizix[42]=250;    diziy[42]=550;
    dizix[43]=350;    diziy[43]=600;
    dizix[44]=450;    diziy[44]=550;
    dizix[45]=550;    diziy[45]=600;
    dizix[46]=650;    diziy[46]=550;
    dizix[47]=750;    diziy[47]=600;
 
    
}/*
int uc()
    {
        
        srand(time(NULL));
        for(int i=0;i<48;i++){
    dizix[i]=rand()%750;   
    diziy[i]=rand()%600;
    for(int j=0;j<48;j++)
    {
         if( dizix[i]-dizix[j]<50|| dizix[j]-dizix[i]<50)
         {
            dizix[i]=rand()%750;       
         }       
         if( diziy[i]-diziy[j]<50|| diziy[j]-diziy[i]<50)
         {
            diziy[i]=rand()%600;       
         }  
    
    }
    
    
    }
    
} */

int main()
{
    harita();
    char harfler[50]; 
    initwindow(850,800); 
    int dugumler[50][50];
    char degiskenler[5];
    int j=0;
      
    for(int i=0;i<50;i++)
      {
              for(int j=0;j<50;j++)
              {
              dugumler[i][j]=0;      
              }
      }
    for(char i='A';i<'Z';i++)
      {
          harfler[j]=i;      
          j++;
      }
      for(char i='a';i<'z';i++)
      {
         if(j==49)
         break;
         harfler[j]=i;
         j++;
      } 
      int harfsayisi=0; // txt belgesindeki toplam harf sayısını hesaplayan değişken
      FILE *dosya;
      dosya = fopen("uzaklik.txt","r");
      int x=50; // döngü içinde koordinatların ayarlanması için gereken değişken
      int dizii[50]; // iki boyutlu dugumler dizisinde küçükten büyüğe sıralatma yapmamız için gereken diziler
      int dizij[50]; // iki boyutlu dugumler dizisinde küçükten büyüğe sıralatma yapmamız için gereken diziler
      int dugum[50]; // iki boyutlu dugumler dizisinde küçükten büyüğe sıralatma yapmamız için gereken diziler
      for(int i=0;i<50;i++)
      {
       dizii[i]=-1; dizij[i]=-1; dugum[i]=-1;        
      }
      int veri=0;
      while( fscanf(dosya,"%s",degiskenler)!=EOF) // txt dosyasınun sonuna kadar
      { 
             outtextxy(780,x,degiskenler); 
             x=x+20;
               for(int i=0;i<50;i++)
               { 
                   if(harfler[i]==degiskenler[0])
                   {
               
                   for(int j=0;j<50;j++)
                  {                               
                    if(harfler[j]==degiskenler[2])
                   {
                                                  
                     char a[3];
                      sprintf(a,"%c",degiskenler[4]);
                      if(degiskenler[5]!=' ')
                      sprintf(a,"%c%c",degiskenler[4],degiskenler[5]);
                      dugumler[i][j]=atoi(a);
                       
                       dugum[veri]=dugumler[i][j]; // 2 boyutlu diziyi tek boyutlu diziye indirgiyor
                       dizii[veri]=i; // 2 boyutlu dizideki i değerini tutuyor
                       dizij[veri]=j;   // 2 boyutlu dizideki j değerini tutuyor
                       veri++;           
                   }                             
                  
                  }                             
                   }
               }
               
      }
      
      
      int dugumsayisi=0;
      int gecici=0;
      for(int i=0;i<veri;i++)
      {
              for(int j=0;j<veri;j++)
              {
               if(dugumler[i][j]!=0)
              {        
              if(i>harfsayisi)
              harfsayisi=i; // harf sayısını buluyor
                if(j>harfsayisi)
              harfsayisi=j; // harf sayısını buluyor
              }
                  if(dugum[i]<dugum[j]) // küçükten büyüğe sıralama işlemi
                  {
                  // düğüm değerlerinin yerini değiştir
                  gecici=dugum[j];
                  dugum[j]=dugum[i];
                  dugum[i]=gecici;
                  // i indisinin yerini değiştir
                  gecici=dizii[j];
                  dizii[j]=dizii[i];
                  dizii[i]=gecici;
                  // j indisinin yerini değiştir
                  gecici=dizij[j];
                  dizij[j]=dizij[i];
                  dizij[i]=gecici; 
                  }
       }  
      
       
      }
     
       int kontrol[veri+1]; // Çevre oluşturmamamız için gerekli dizi
       for(int i=0;i<veri+1;i++)
      {
      kontrol[i]=-1;       // varsayılan kontrol değerlerini -1 yaptık
      }
      
     for(int i=0;i<veri+1;i++)
       {
               if(i%3==0)
              setcolor(YELLOW);  
              if(i%3==1)
              setcolor(RED);  
              if(i%3==2)
              setcolor(GREEN);  
               if(kontrol[dizii[i]]==-1&&kontrol[dizij[i]]==-1) // sıralanmış dizidi iki nokta da *1 se çizgi çek ve noklara 2 ata
               {
                moveto(dizix[dizii[i]],diziy[dizii[i]]);  
                lineto(dizix[dizij[i]],diziy[dizij[i]]);   
                kontrol[dizii[i]]=2;
                kontrol[dizij[i]]=2;
                
                 moveto(dizix[dizii[i]],diziy[dizii[i]]);  
                lineto(dizix[dizij[i]],diziy[dizij[i]]);   
               
                
                 printf("\n----%d--%d-----",dizii[i],dizij[i]); 
               }
              else if(kontrol[dizii[i]]==-1||kontrol[dizij[i]]==-1) // sıralanmış dizide noktalardan biri -1 se çizgi çek ve noktalara 1 ata
               {
                  
                moveto(dizix[dizii[i]],diziy[dizii[i]]);  
                lineto(dizix[dizij[i]],diziy[dizij[i]]);   
                kontrol[dizii[i]]=1;
                kontrol[dizij[i]]=1;
                 printf("\n----%d--%d-----",dizii[i],dizij[i]); 
               }
              
                else    if(kontrol[dizii[i]]>1&&kontrol[dizij[i]]>1) // noktalar 1 den büyükse çevre oluşturmaz ve çizgi çekebiliriz ve 1 ata
                   {
                    moveto(dizix[dizii[i]],diziy[dizii[i]]);  
                    lineto(dizix[dizij[i]],diziy[dizij[i]]);   
                    kontrol[dizii[i]]=1;
                    kontrol[dizij[i]]=1;
                    
                     moveto(dizix[dizii[i]],diziy[dizii[i]]);  
                    lineto(dizix[dizij[i]],diziy[dizij[i]]);   
                   
                    
                     printf("\n----%d--%d-----",dizii[i],dizij[i]); 
                   }   
                
               
             //  printf("\n----%d--%d--%d-----",dugum[i],dizii[i],dizij[i]);
       }
       int dizi[harfsayisi];
      printf("111 %d 111",harfsayisi);
      
        for(int i=0;i<harfsayisi+1;i++) // koordinatlar üzerinde harfleri yazdırıyor
{
         setcolor(WHITE);
              readimagefile("siyah.jpg",dizix[i],diziy[i],dizix[i]+5,diziy[i]+5);
             char dnokta[30];
             sprintf(dnokta,"%c",harfler[i]);
             outtextxy(dizix[i],diziy[i],dnokta); 

}

      fclose(dosya);
 
 
 
      getch();
}
