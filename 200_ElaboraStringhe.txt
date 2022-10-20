using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


namespace ConsoleApp_GestioneStringhe
{
    class Program
    {
        static void Main(string[] args)
        {
            string indirizzoIPbase = "";

            //Inserimento da console dell'indirizzo IP su cui lavorare
            Console.WriteLine("Scrivi l'indirizzo IP che vuoi analizzare");
            string indirizzoIPInserito = Console.ReadLine();
            

            //Indentificazione del carattere da cui inizia il quarto ottetto (ossia l'ultimo numero)

            //Con un ciclo FOR cerchiamo la terza occorrenza del carattere "." nella stringa dell'indirizzo IP
            int posizioneTerzoPunto = 0;
            for (int i = 0; i < 3; i++)
            {
                posizioneTerzoPunto = indirizzoIPInserito.IndexOf(".", posizioneTerzoPunto + 1); //ricerca dei caratteri "." nella stringa dell'indirizzo IP.
            }

            //Estrapolo una stringa che contiene solo la base dell'indirizzo IP
            indirizzoIPbase = indirizzoIPInserito.Substring(0, posizioneTerzoPunto + 1);
            Console.WriteLine("\nI primi 3 ottetti dell'indirizzo IP sono:\n" + indirizzoIPbase + "\n");

            //Estrapolo la stringa che contiene solo l'ultimo ottetto dell'indirizzo IP
            string indirizzoIPfinale = indirizzoIPInserito.Substring(posizioneTerzoPunto+1);
            Console.WriteLine("L'ultimo ottetto dell'indirizzo IP inserito è:\n" + indirizzoIPfinale + "\n");

            //Definisco quindi i primi 3 indirizzi IP da assegnare su quella rete
            int indirizzoIPPrimoNodo = Int32.Parse(indirizzoIPfinale); //Trasformo in INT la stringa in modo da poterci lavorare con formule matematiche
            int indirizzoIPSecondoNodo = indirizzoIPPrimoNodo + 1;
            int indirizzoIPTerzoNodo = indirizzoIPPrimoNodo + 2;

            //Realizzo le stringhe degli IP del secondo e terzo device
            string indirizzoIPdevice2 = string.Concat(indirizzoIPbase, indirizzoIPSecondoNodo); //Concateno la stringa della base con il quarto ottetto
            string indirizzoIPdevice3 = string.Concat(indirizzoIPbase, indirizzoIPTerzoNodo);
           
            Console.WriteLine("I 2 indirizzi IP successivi a quello inserito sono:\n" + indirizzoIPdevice2 + "\n" + indirizzoIPdevice3);
            Console.ReadLine();


        }
    }
}