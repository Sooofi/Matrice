# Matrice
import Input.*;
public class Matrice
{
        static int dimr=4,dimc=2,n,scelta;
        static Gest_Input input=new Gest_Input();
        static Righe cor_rig,inizio;
        static Colonne cor_col;
    public static void main(String args[])
    {
        do
        {
            System.out.println("Quale operzione vuoi esegire?");
            System.out.println("1) Inserimento matrice");
            System.out.println("2) stampa");
            System.out.println("3) EXIT");
            scelta=Integer.valueOf(input.read());
            switch(scelta)
            {
                case 1:
                        inserimento();                      
                        break;
                case 2:
                        stampa();
                        break;
                case 3:
                       System.out.println("FINE PROGRAMMA XD");
                       break;
                
            }
        }while(scelta!=3);
    
    }
     
      static void inserimento()
      {
            for(int i=0;i<dimr;i++)
            {
                System.out.println("Inserire numero nella cella riga");
                n=Integer.valueOf(input.read()); 
                Righe riga=new Righe(n);
                
                if(i==0)
                {
                     cor_rig=riga;
                     inizio=cor_rig;
                }
                else
                {
                     if(inizio.nextr==null)
                        {
                            inizio.nextr=riga;
                            cor_rig=inizio.nextr;
                        }
                     else
                        {
                            cor_rig.nextr=riga;
                            cor_rig=cor_rig.nextr;
                        }
                }
                
                for(int j=0;j<dimc;j++)
                {                   
                    System.out.println("Inserire numero nella cella colonna");
                    n=Integer.valueOf(input.read());
                    Colonne colonna=new Colonne(n);
                    if(cor_rig.nextc==null)
                            {
                                inizio.nextc=colonna;
                                cor_col=inizio.nextc;
                            }
                    else
                        if(j==0)
                        {
                               cor_rig.nextc=colonna;
                               cor_col=cor_rig.nextc;
                        }
                        else   
                            {
                                cor_col.nextc=colonna;
                                cor_col=cor_col.nextc;
                            }
                }
            }
        }
        static void stampa()
        {
            cor_rig=inizio;
            for(int i=0;i<dimr;i++)
            {
                System.out.println(" "+cor_rig.cont);
               
                for(int j=0;j<dimc;j++)
                {
                  cor_col=cor_rig.nextc;
                  System.out.println(" "+cor_col.cont);
                }
                 cor_rig=cor_rig.nextr;
            }
        }
}
