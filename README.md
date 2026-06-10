# ZADACI SA ISPITA

<details>
<summary><strong>Napišite program za pronalaženje faktorijela bilo kojeg broja.
</strong></summary>
	
```java
import java.util.Scanner;
class Main {
    public static void main(String[] args) {
        int unos = 0;
        Scanner input = new Scanner(System.in);
        System.out.println("Unesite broj: ");
        unos = input.nextInt();

        int rezultat = faktorijel(unos);
        System.out.println("Faktorijel broja " + unos + " je: " + rezultat);
    }

    public static int faktorijel(int unos){
        int fakt = 1;
        for(int i = 1; i <= unos; i++){
            fakt *= i;
        }
        return fakt;
    }
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Putem tipkovnice upisuju se dva broja. Napišite program za pronalaženje vrijednosti jednog broja podignutog na potenciju drugog.</strong></summary>
	
```java
import java.util.Scanner;
class Main {
    public static void main(String[] args) {
        int a,b;
        Scanner input = new Scanner(System.in);
        System.out.println("Unesite vrijednost 1. broja: ");
        a = input.nextInt();
        System.out.println("Unesite potenciju: ");
        b = input.nextInt();
        
        //System.out.println(b + " potencija broja " + a + " je " + Math.pow(a, b));
        int poziv = potencija(a,b);
        System.out.println("Rezultat je: " + poziv);
    }
    
    public static int potencija(int a, int b){
        int rezultat = 1;
        for(int i=1; i<=b; i++){
            rezultat *=a;
        }
        return rezultat;
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Napišite do-while petlju koja od korisnika traži da unese dva broja. Brojeve treba zbrojiti i prikazati zbroj. Petlja bi trebala pitati korisnika želi li on ili ona ponovno izvesti operaciju. Ako je tako, petlja bi se trebala ponoviti; inače bi trebao prekinuti.</strong></summary>
	
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char ponovi = 'd'; // Postavljamo na 'd' da bi se petlja barem jednom izvršila
        
        do {
            System.out.print("Unesite prvi broj: ");
            int broj1 = scanner.nextInt();
            System.out.print("Unesite drugi broj: ");
            int broj2 = scanner.nextInt();
            
            int zbroj = broj1 + broj2;
            System.out.println("Zbroj brojeva je: " + zbroj);
            
            System.out.print("Želite li ponovno izvršiti operaciju? (da/d ne/n): ");
            String unos = scanner.next();
            ponovi = unos.charAt(0);
            
        } while (ponovi == 'd' || ponovi == 'D' || ponovi == 'y' || ponovi == 'Y');
        
        scanner.close();
    }
}
```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Napisati program koji će imati sljedeće mogućnosti odabira (koristiti switch):
(1) Izračunati aritmetičku sredinu sporedne dijagonale.
(2) Izračunati sumu neparnih elemenata prvog retka i prvog stupca matrice. Ukoliko ne postoje neparni elementi ispisati da nije bilo moguće izračunati sumu. 
(3) Ispisati sve brojeve na parnim indeksima vektora V (koristiti continue). 
Program na početku treba od korisnika zatražiti unos maksimalnog broja elemenata (n) vektora V kao dimenzije kvadratne matrice (mxm). Koristeći do-while petlju ograničiti unos broja elemenata (n) na interval između 2 i 10, a za kvadratnu matricu broj (m) ograničiti na interval između 1 i 5. Unos se mora ponavljati sve dok nije unesen broj u traženom intervalu. Koristiti try-catch blokove za zaštitu od grešaka kao što je npr. unos znaka na mjesto unošenja dimenzija vektora i matrice.</strong></summary>
	
```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class Main {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        int n = 0;
        int m = 0;
        int izbor;

        // Unos dimenzije vektora (2-10)
        do {
            try {
                System.out.print("Unesite broj elemenata vektora V (2-10): ");
                n = input.nextInt();

                if (n < 2 || n > 10) {
                    System.out.println("Broj mora biti između 2 i 10!");
                }

            } catch (InputMismatchException e) {
                System.out.println("Greška! Morate unijeti cijeli broj.");
                input.nextLine();
            }

        } while (n < 2 || n > 10);

        // Unos elemenata vektora
        double[] V = new double[n];

        System.out.println("\nUNOS ELEMENATA VEKTORA");

        for (int i = 0; i < n; i++) {
            while (true) {
                try {
                    System.out.print("V[" + i + "] = ");
                    V[i] = input.nextDouble();
                    break;
                } catch (InputMismatchException e) {
                    System.out.println("Greška! Unesite broj.");
                    input.nextLine();
                }
            }
        }

        // Unos dimenzije matrice (1-5)
        do {
            try {
                System.out.print("\nUnesite dimenziju kvadratne matrice (1-5): ");
                m = input.nextInt();

                if (m < 1 || m > 5) {
                    System.out.println("Dimenzija mora biti između 1 i 5!");
                }

            } catch (InputMismatchException e) {
                System.out.println("Greška! Morate unijeti cijeli broj.");
                input.nextLine();
            }

        } while (m < 1 || m > 5);

        // Unos matrice
        double[][] matrica = new double[m][m];

        System.out.println("\nUNOS ELEMENATA MATRICE");

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {

                while (true) {
                    try {
                        System.out.print("M[" + i + "][" + j + "] = ");
                        matrica[i][j] = input.nextDouble();
                        break;
                    } catch (InputMismatchException e) {
                        System.out.println("Greška! Unesite broj.");
                        input.nextLine();
                    }
                }
            }
        }

        // Izbornik
        while (true) {
            System.out.println("1. Aritmetička sredina sporedne dijagonale");
            System.out.println("2. Suma neparnih elemenata prvog retka i prvog stupca");
            System.out.println("3. Ispis elemenata na parnim indeksima vektora");
            System.out.println("4. Izlaz");

            try {
                System.out.print("Odaberite opciju: ");
                izbor = input.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Greška! Unesite broj od 1 do 4.");
                input.nextLine();
                continue;
            }

            switch (izbor) {

                case 1:

                    double sumaDijagonale = 0;
                    for (int i = 0; i < m; i++) {
                        sumaDijagonale += matrica[i][m - 1 - i];
                    }
                    double aritmetickaSredina = sumaDijagonale / m;
                    System.out.println("Aritmetička sredina sporedne dijagonale iznosi: "
                            + aritmetickaSredina);
                    break;

                case 2:

                    double suma = 0;
                    boolean postojiNeparan = false;
                    // prvi redak
                    for (int i = 0; i < m; i++) {
                        if (matrica[0][i] % 2 != 0) {
                            suma += matrica[0][i];
                            postojiNeparan = true;
                        }
                    }

                    // prvi stupac
                    for (int i = 0; i < m; i++) {
                        // preskačemo [0][0] da se ne zbroji dva puta
                        if (i == 0) {
                            continue;
                        }
                        if (matrica[i][0] % 2 != 0) {
                            suma += matrica[i][0];
                            postojiNeparan = true;
                        }
                    }
                    if (postojiNeparan) {
                        System.out.println("Suma neparnih elemenata prvog retka i prvog stupca iznosi: "
                                + suma);
                    } else {
                        System.out.println("Nije bilo moguće izračunati sumu jer nema neparnih elemenata.");
                    }

                    break;

                case 3:

                    System.out.println("Elementi na parnim indeksima:");
                    for (int i = 0; i < n; i++) {

                        if (i % 2 != 0) {
                            continue;
                        }
                        System.out.println("V[" + i + "] = " + V[i]);
                    }
                    break;

                case 4:

                    System.out.println("Program završen.");
                    input.close();
                    System.exit(0);
                    break;

                default:
                    System.out.println("Neispravan odabir! Unesite broj od 1 do 4.");
            }
        }
    }
}

```
</details>

---
<br>
<br>
 
<details>
<summary><strong>Neka su zadane kvadratne matrice A i B s N redaka i N stupaca. Napisati funkciju koja kao parametre prima dvije matrice i računa i ispisuje na ekran sumu njihovih glavnih dijagonala. Možemo pretpoataviit da su matrice vec popunjene.</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		int n;
		
		System.out.println("Unesite velicinu kvadratne matrice A i B: ");
		n=input.nextInt();
		
	
		int A [][] = new int [n][n];
		int B [][] = new int [n][n];
		
		System.out.println("Unesite elemente kvadratne matrice A: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        A[i][j]=input.nextInt();
		    }
		}
		
		System.out.println("Unesite elemente kvadratne matrice B: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        B[i][j]=input.nextInt();
		    }
		}
		
		System.out.println("Matrica A: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        System.out.print(A[i][j] + " ");
		    }
		    System.out.println();
		}
		
		System.out.println("Matrica B: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        System.out.print(B[i][j] + " ");
		    }
		    System.out.println();
		}
		
		funkcija(A, B, n);
	}
	
	public static void funkcija(int A[][], int B[][], int n){
	    int suma = 0;
	    
	    for(int i=0; i<n; i++){
	        suma += A[i][i];
	        suma += B[i][i];
	    }
	    
	    System.out.println("Suma iznosi: " +suma);
	}
}

```
</details>

---
<br>
<br>
 
<details>
<summary><strong>Neka je zadana kvadratna matrica A s N redaka i N stupaca. Napisati funkciju koja kao parametar prima matricu i računa sumu glavne i sporedne dijagonale. Na ekran je potrebno ispisati koja je suma veda, mozemmo pretpostaviti da je matrrica ved popunjena </strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		int n;
		
		System.out.println("Unesite velicinu kvadratne matrice A: ");
		n=input.nextInt();
		
	
		int A [][] = new int [n][n];
		
		System.out.println("Unesite elemente kvadratne matrice A: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        A[i][j]=input.nextInt();
		    }
		}
		
		
		System.out.println("Matrica A: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        System.out.print(A[i][j] + " ");
		    }
		    System.out.println();
		}
		

		
		funkcija(A, n);
	}
	
	public static void funkcija(int A[][], int n){
	    int suma = 0;
	    int suma2 = 0;
	    
	    for(int i=0; i<n; i++){
	        suma += A[i][i];
	        suma2 += A[i][n - 1 - i];
	    }
	    
	    
	    System.out.println("Suma glavne dijagonale: " +suma);
	    System.out.println("Suma sporedne dijagonale: " +suma2);
	    
	    if(suma > suma2){
    		System.out.println("Suma glavne dijagonale je veća");
		}
		else if(suma2 > suma){
    		System.out.println("Suma sporedne dijagonale je veća");
		}
		else{
    		System.out.println("Sume dijagonala su jednake");
		}
	    }
	}
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Korisnik unosi dva broja: m i n (stupci i retci matrice) i nakon toga unosi vrijedost matrice. Ukoliko je matrica kvadratna(mxn) računa srednju vrijednost brojeva glavne dijagonale. UKOLIKO NIJE Kvadratna, računa srednju vrijednost 1. Stupca ili retka(ovisno što jevede: ukoliko ima više stupaca-računa na stupce, ukoliko ima više redaka računa za retke.</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
	    Scanner input = new Scanner(System.in);
	    int m,n;
	    
	    System.out.println("Unesite broj stupaca matrice: ");
	    m=input.nextInt();
	    
	    System.out.println("Unesite broj redaka matrice: ");
	    n=input.nextInt();
	    
	    System.out.println("Popunite matricu: ");
	    int A [][] = new int [n][m];
	    
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            A[i][j]=input.nextInt();
	        }
	    }
	    
	    System.out.println("Matrica izgleda ovako: ");
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            System.out.print(A[i][j] + " ");
	        }
	        System.out.println();
	    }   
	    funkcija(A,n,m);
    }
    
    public static void funkcija(int A[][], int n, int m){
    int suma = 0;
    int suma2 = 0;
    int suma3 = 0;

    if(m == n){

        for(int i = 0; i < n; i++){
            suma += A[i][i];
        }
        double avg = (double)suma / n;
        System.out.println("Srednja vrijednost glavne dijagonale je: " + avg);

    }else if(n > m){
        for(int i = 0; i < n; i++){
            suma2 += A[i][0];
        }
        double avg2 = (double)suma2 / n;
        System.out.println("Srednja vrijednost 1. stupca je: " + avg2);

    }else{
        for(int j = 0; j < m; j++){
            suma3 += A[0][j];
        }

        double avg3 = (double)suma3 / m;
        System.out.println("Srednja vrijednost 1. retka je: " + avg3);
    	}
	}
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Korisnik pogađa vrijednost broja definiranog u programu (može biti predefiniran, kao konstanta). Računalo mu vrada poruke veci/manji dok god ga ne pogodi. Kada ga pogodi, ispiše mu broj pokušaja (npr. “Bravo! Pogodio/la si broj zadan u programu, trebalo ti je 7 pokušaja”).</strong></summary>
	
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        final int TRAZENI_BROJ = 42;
        int pokusaji = 0; 
        Scanner input = new Scanner(System.in);
        
        System.out.println("Pogodi broj od 1 do 100:");

        while (1==1) {
            int unos = input.nextInt();
            pokusaji++;

            if (unos == TRAZENI_BROJ) {
                System.out.println("Bravo! Pogodio/la si broj zadan u programu, trebalo ti je " + pokusaji + " pokušaja.");
                break;
            } else if (unos < TRAZENI_BROJ) {
                System.out.println("Traženi broj je veći. Pokušaj ponovo.");
            } else {
                System.out.println("Traženi broj je manji. Pokušaj ponovo.");
            }
        }

        input.close();
    }
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Potrebno je napisati program u Javi koji će cjelobrojnu kvadratnu matricu A (max 100 elemenata) s N redaka i N stupaca provjeriti da li se radi o magičnom kvadratu (jednak zbroj po redovima, stupcima I dijagonalama). Ako se radi o magičnom kvadratu na ekran se ispisuje 1, u suprotnom se ispisuje -1. Uz navadeni broj potrebno je ispisati I sumu znamenki u prvom redu matrice.</strong></summary>
	
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        int n;
        System.out.println("Unesite kvadratnu matricu A (max 100 elemenata): ");
        n = input.nextInt();
        
        if (n <= 0 || n * n > 100) {
            System.out.println("Ponovite unos! Veličina matrice je max 100 elemenata ");
            return;
        }
        
        System.out.println("Unesite elemente matrice: " + n + "x" + n);
        int A[][] = new int[n][n];
        int sumaZnamenkiPrvogReda = 0;
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                A[i][j] = input.nextInt();
                // da bi se samo izracunao prvi red (i je red, a indeksi krecu od 0)
                if (i == 0) {
                    // Računanje sume znamenki prvog reda
                    sumaZnamenkiPrvogReda += sumaZnamenki(A[i][j]);
                }
            }
        }
        
        // Provera da li se radi o magičnom kvadratu
        int sumaPrvogReda = sumaReda(A[0]);
        boolean magicniKvadrat = true;
        
        for (int i = 1; i < n; i++) {
            if (sumaReda(A[i]) != sumaPrvogReda || sumaStupca(A, i) != sumaPrvogReda) {
                magicniKvadrat = false;
                break;
            }
        }
        
        int sumaDijagonale1 = sumaDijagonale(A, true);
        int sumaDijagonale2 = sumaDijagonale(A, false);
        
        if (!magicniKvadrat || sumaDijagonale1 != sumaPrvogReda || sumaDijagonale2 != sumaPrvogReda) {
            System.out.println("-1");
        } else {
            System.out.println("1");
        }
        
        // Ispis sume znamenki prvog reda
        System.out.println(sumaZnamenkiPrvogReda);
    }
    
    // Metoda za računanje sume znamenki broja
    public static int sumaZnamenki(int broj) {
        int suma = 0;
        while (broj != 0) {
            suma += broj % 10;
            broj /= 10;
        }
        return suma;
    }
    
    // Metoda za računanje sume reda
    public static int sumaReda(int[] red) {
        int suma = 0;
        for (int broj : red) {
            suma += broj;
        }
        return suma;
    }
    
    // Metoda za računanje sume stupca
    public static int sumaStupca(int[][] matrica, int indeksStupca) {
        int suma = 0;
        for (int i = 0; i < matrica.length; i++) {
            suma += matrica[i][indeksStupca];
        }
        return suma;
    }
    
    // Metoda za računanje sume dijagonale (dijagonala1 ako je dijagonala=true, dijagonala2 ako je dijagonala=false)
    public static int sumaDijagonale(int[][] matrica, boolean dijagonala) {
        int suma = 0;
        if (dijagonala) {
            for (int i = 0; i < matrica.length; i++) {
                suma += matrica[i][i];
            }
        } else {
            for (int i = 0; i < matrica.length; i++) {
                suma += matrica[i][matrica.length - 1 - i];
            }
        }
        return suma;
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koji će za cjelobrojnu kvadratnu matricu A(max 100 elemenata) s N redaka I N stupaca izračunati sumu svih znamenki iznad glavne dijagonale, uključujući I glavnu dijagonalu.</strong></summary>
	
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        int n;
        System.out.println("Unesite dimenziju kvadratne matrice A:");
        n = input.nextInt();

        // maksimalno 100 elemenata
        if (n <= 0 || n * n > 100) {
            System.out.println("Matrica smije imati najviše 100 elemenata!");
            return;
        }

        int[][] A = new int[n][n];
        System.out.println("Unesite elemente matrice:");

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print("A[" + i + "][" + j + "] = ");
                A[i][j] = input.nextInt();
            }
        }
        System.out.println("\nMatrica:");

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(A[i][j] + "\t");
            }
            System.out.println();
        }
        int suma = 0;

        // elementi na i iznad glavne dijagonale
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                suma += sumaZnamenki(A[i][j]);
            }
        }
        System.out.println("\nSuma svih znamenki iznad glavne dijagonale");
        System.out.println("(uključujući glavnu dijagonalu) iznosi: " + suma);
        input.close();
    }
    // funkcija za računanje sume znamenki jednog broja
    public static int sumaZnamenki(int broj) {

        broj = Math.abs(broj);
        int suma = 0;

        if (broj == 0) {
            return 0;
        }
        while (broj != 0) {
            suma += broj % 10;
            broj /= 10;
        }
        return suma;
    }
}
```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koji će za kvadratnu matricu pokrenuti N niti (jedan red matrice = jedna nit). Svaka nit bi trebala imati dodjeljeno ime u obliku “Nit 0; Nit 1; Nit 2; itd…” te bi trebala izračunati sumu dodjeljenog reda matrice I ispisati je u obliku npr “Nit 0 suma = 22”. Napomena: niti se trebaju izvršavati u redoslijedu kako su pokrenute.</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		System.out.println("Unesi matricu: ");
		int n;
		n=input.nextInt();
		
		int A[][]=new int[n][n];
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        A[i][j]=input.nextInt();
		    }
		}
		
		//NAPRAVI POLJE NITI OBAVEZNO!!!
	    Thread[] thread = new Thread[n];
	    
	    //POLJU NITI DODIJELI STA SVAKA NIT TREBA RADITI
	    for(int i=0;i<n;i++){
	        thread[i]= new Thread(new racun(A[i],i,n));
	    }
	    
		
		for(int i=0;i<n;i++){
		    //POKRENE NITI
		    thread[i].start();
		    try{
		        //DA SE REDOM IZVRSAVAJU
		        thread[i].join();
		    }catch(InterruptedException e){
		        e.printStackTrace();    
		    }
		    
		}
		
		System.out.println("Matrica izgleda ovako: ");
		for(int i=0; i<n; i++){
		    for(int j=0; j<n; j++){
		        System.out.print(A[i][j] + " ");
		    }
		    System.out.println();
		}
		
	}
}

class racun implements Runnable{
    int[] redak;
    int index;
    int n;
    
    public racun(int[] redak, int index, int n){
        this.redak=redak;
        this.index = index;
        this.n=n;
    }
    
    public void run(){
    
    int suma=0;
    for(int i=0;i<n;i++){
        suma+=redak[i];
        
    }
    
    System.out.println("Nit " + index + " suma = "+ suma);
    }
    
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koji će za učitanu matricu A ispisati transponiranu matricu na standardni izlaz</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
	    Scanner input = new Scanner(System.in); 
	    int n, m;
	    
	    System.out.println("Unesite koliko redova matrica da ima: ");
	    n=input.nextInt();
	    System.out.println("Unesite koliko stupaca matrica da ima: ");
	    m=input.nextInt();
	    
	    int A [] [] = new int [n][m];
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            System.out.println("Unesite matricu " + i + " x " + j);
	            A[i][j]=input.nextInt();
	        }
	    }
	    
	    System.out.println("Matrica izgleda ovako: ");
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            System.out.println(A[i][j]);
	        }
	    }
	    
	    trans(A,n,m);
	    System.out.println("Transponirana matrica: ");
	    int C [][] = trans(A,n,m);
	
	    for(int i=0; i<m; i++){
	        for(int j=0; j<n; j++){
	            System.out.println(C[i][j]);
	        }
	    }
	    input.close();
	}
	
	
	
	public static int[][] trans (int A[][], int n, int m){
	    int B [] [] = new int[m][n];
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            B[j][i]=A[i][j];
	        }
	    }
	    return B;
	}
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Potrebno je napisati program u Javi koji će za cjelobrojnu kvadratnu matricu A (max 100 elemenata) s N redaka I N stupaca usporediti sumu elemenata iznad I ispod sporedne dijagonale (ne računajući elemente na sporednoj dijagonali). Funkcija treba vratiti 1 ako je suma elemenata iznad veća od sume elemenata ispod, odnosno -1 ako je obrnut slučaj I 0 ako su jednake sume.</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
	 Scanner input = new Scanner(System.in);
	 int n;
	 System.out.println("Unesite cjelobrojnu kvadratnu matricu A: ");
	 n=input.nextInt();
	 if(n<=0 || n>100){
	     System.out.println("Greska");
	     return;
	 }
	 
	 int A[][] = new int [n][n];
	 System.out.println("Popunite matricu: ");
	 for(int i=0; i<n; i++){
	     for(int j=0; j<n; j++){
	         A[i][j] = input.nextInt();
	     }
	 }
	 
	 System.out.println("Matrica izgleda ovako: ");
	 for(int i=0; i<n; i++){
	     for(int j=0; j<n; j++){
	         System.out.print(A[i][j] + " ");
	     }
	     System.out.println();
	 }
	 int dijagonala = funkcija(A,n);
	 System.out.println(dijagonala);
  }
  
  public static int funkcija(int A[][], int n){
      int suma2 = 0;
      int suma3 = 0;
      //elementi iznad i ispod sporedne dijagonale
      for(int i=0; i<n; i++){
          for(int j=0; j<n; j++){
              if(j < n - i - 1){
                  suma2 += A[i][j];
              }else if(j > n - i - 1){
                  suma3 += A[i][j];
              }
          }
      }
      System.out.println("Suma elemenata iznad sporedne dijagonale: " +suma2);
      System.out.println("Suma elemenata ispod sporedne dijagonale: " +suma3);
      if(suma2>suma3){
          return 1;
      }else if(suma3>suma2){
          return -1;
      }else{
          return 0;
      }
   }
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Potrebno je napisati program u Javi koji će za zadanu rečenicu pokrenuti N niti (jedna riječ = jedna nit). Svaka nit bi trebala imati dodijeljeno ime u obliku “Nit 0; Nit 1;…” te bi trebala izračunati sumu ASCII vrijednosti slova zadane riječi I ispisati je u obliku “Nit 0 suma = 100”. Napomena: niti se trebaju izvršavati jedna za drugom.
</strong></summary>
	
```java 
import java.util.Scanner;
public class Main
{
    public static void main(String[] args){
        Scanner input = new Scanner(System.in);
        System.out.println("Unesi recenicu: ");
        String recenica = input.nextLine();
        
        //s+ trazi space
        String [] rijeci = recenica.split("\\s+");
        
        //nadje koliko ima elemenata (rijeci)
        int n = rijeci.length;
        Thread thread[] = new Thread[n];
        
        for(int i=0; i<n; i++){
            thread[i] = new Thread(new nit(rijeci[i], i));
        }
        
        for(int i=0; i<n; i++){
            thread[i].start();
            try{
                thread[i].join();
            }catch(Exception e){
                e.printStackTrace();
            }
        }
        
    }
}
class nit implements Runnable{
    String rijec;
    int index;
    public nit(String rijec, int index){
        this.rijec=rijec;
        this.index=index;
    }
    
    public void run(){
        int suma=0;
        for(int i=0; i<rijec.length(); i++ ){
            suma+=rijec.charAt(i);
        }
        System.out.println("Nit " + index + " Suma = " + suma);
    }
}

```
</details>

---
<br>
<br>

<details>
<summary><strong>Potrebno je napisati program u Javi koji će za kvadratnu matricu A s N redaka I N stupaca koja u sebi ima samo nule I jedinice izračunati koliko ima pojavljivanja broja 0, a da su oko njega sve jedinice.</strong></summary>
	
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.println("Unesite dimenziju kvadratne matrice:");
        int n = input.nextInt();
        
        int[][] matrica = new int[n][n];
        
        System.out.println("Unesite elemente matrice (samo 0 ili 1):");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int unos;
                do {
                    System.out.print("Unesite element [" + i + "][" + j + "]: ");
                    unos = input.nextInt();
                    if (unos != 0 && unos != 1) {
                        System.out.println("Unesite samo 0 ili 1.");
                    }
                } while (unos != 0 && unos != 1);
                matrica[i][j] = unos;
            }
        }
        
        System.out.println("Uneta matrica:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(matrica[i][j] + " ");
            }
            System.out.println();
        }
        
        int brojac = brojPojavljivanja(matrica,n);
        System.out.println("Broj pojavljivanja broja 0 okruženog 1 je: " +brojac);
        input.close();
    }
    
    public static int brojPojavljivanja(int A [][], int n){
        int brojac=0;
        for(int i=1; i<n-1; i++){
            for(int j=1; j<n-1; j++){
                if(A[i][j] == 0 && A[i-1][j] == 1 && A[i+1][j] == 1 && A[i][j-1] == 1 && A[i][j+1] == 1){
                    brojac++;
                }
            }
        }
        return brojac;
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koji će sa standardnog ulaza učitati broj N koji predstavlja dimenzije matrice A[N][N]. Nakon toga potrebno je stvoriti N niti koje će obraditi matricu (niti se trebaju izvršavati jedna iza druge, odnosno, sljedeća treba čekati izvršavanje prethodne – broj niti trebao bi odgovarati broju elemenata na glavnoj dijagonali). Svaka nit bi trebala imati dodijeljeno ime u obliku “Nit 1”, “Nit 2”… te bi trebala izračunati sumu elemenata vertikalno (prema dolje) od elemenata glavne dijagonale.</strong></summary>
	
```java
import java.util.Scanner;
public class Main
{
    public static void main(String[] args){
        Scanner input = new Scanner(System.in);
        int n;
        
        System.out.println("Unesi matricu: ");
        n = input.nextInt();
        
        int A[][] = new int[n][n];
        System.out.println("Unesite elemente: ");
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                A[i][j] = input.nextInt();
            }
        }
        
        System.out.println("Matrica izgleda ovako: ");
         for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                System.out.print(A[i][j] + " ");
            }
            System.out.println();
            }
        Thread thread[]  = new Thread[n];
        
        
        //PREDAJEMO NITI CIJELU MATRICU JER STUPAC NE MOŽE, SAMO REDAK
        for(int i=0;i<n;i++){
                thread[i]=new Thread(new dijagonala(A,i,n));
            }
        
        for(int i=0;i<n;i++){
            thread[i].start();
            try{
                thread[i].join();
            }catch(Exception e){
                e.printStackTrace();
            }
        }
        
    }
}

class dijagonala implements Runnable{
    int A[][];
    int index, n;
    public dijagonala(int A[][], int index, int n){
        this.index = index;
        this.n = n;
        this.A = A;
    }
    public void run(){
        int suma = 0;
        
        //ZBRAJA SE SA INDEXOM JER ŽELIMO SAMO ELEMENTE GLAVNE DIJAGONALE I ISPOD  NJE
        for(int i=0+index; i<n; i++){
            //INDEX OZNACAVA STUPAC, A i REDAK
            suma+=A[i][index];
        }
    System.out.println("Nit " + index + " suma = " + suma);
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koja će matricu A ispisati u printu zmijskog uzorka.</strong></summary>
	
```java
import java.util.Scanner;
public class Main{
public static void main(String[] args) {
	    Scanner input = new Scanner(System.in); 
	    int n, m;  
	    System.out.println("Unesite koliko redova matrica da ima: ");
	    n=input.nextInt();
	    System.out.println("Unesite koliko stupaca matrica da ima: ");
	    m=input.nextInt();  
	    int A [] [] = new int [n][m];
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            System.out.println("Unesite matricu " + i + " x " + j);
	            A[i][j]=input.nextInt();
	        }
	    }
	    System.out.println("Matrica izgleda ovako: ");
	    for(int i=0; i<n; i++){
	        for(int j=0; j<m; j++){
	            System.out.println(A[i][j]);
	        }
	    }
	    System.out.println("Zmijski uzorak: ");
	    zmija(A,n,m);
	    
	    input.close();
	}
	
	public static void zmija(int A[][], int n, int m){
	    for(int i=0; i<n; i++){
	        if(i%2==0){
	            for(int j=0; j<m; j++){
	                System.out.println(A[i][j]);
	            }
	        }else{
	            for(int j=m-1; j>=0; j--){
	                System.out.println(A[i][j]);
	            }
	        }
	    }
	}
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Napisati matricu n x m u spiralnom obliku</strong></summary>
	
```java
import java.util.Scanner;
public class Main {
    
    // Function to print a 2D array in spiral order
    public static void printSpiral(int[][] matrix) {
        if (matrix.length == 0) {
            return;
        }

        int top = 0;
        int bottom = matrix.length - 1;
        int left = 0;
        int right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            // Print top row
            for (int i = left; i <= right; i++) {
                System.out.print(matrix[top][i] + " ");
            }

            top++;

            // Print right column
            for (int i = top; i <= bottom; i++) {
                System.out.print(matrix[i][right] + " ");
            }

            right--;

            // Print bottom row if it still exists
            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    System.out.print(matrix[bottom][i] + " ");
                }
                bottom--;
            }

            // Print left column if it still exists
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    System.out.print(matrix[i][left] + " ");
                }
                left++;
            }
        }
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n,m;
        System.out.println("Unesite broj redaka matrice: ");
        n=input.nextInt();
        
        System.out.println("Unesite broj stupaca matrice: ");
        m=input.nextInt();
        
        System.out.println("Popunite matricu ");
        int[][] matrix = new int [n][m];
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                matrix[i][j]=input.nextInt();
            }
        }
        
        System.out.println("Matrica izgleda ovako: ");
         for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
        printSpiral(matrix);
    }
}

```
</details>

---
<br>
<br>

# PREDROK ZADACI

	
<details>
<summary><strong> Potrebno je napisati program u Javi koji će za kvadratnu matricu A s N redaka i stupaca * koja u sebi ima samo nule i jedinice izračunati koliko ima pojavljivanja broja 0, a da su oko njega sve jedinice.</strong></summary>
	
```java
import java.util.Scanner;

public class Main { 
public static void main(String[] args) {
    Scanner scanner = new Scanner(System. in);
    System.out.println(x : "Unesi N:");
    int n = scanner.nextInt();
    int[][] matrica = new int[n][n];
    System.out.println(x : "Unesi elemente matrice: samo 0 ili 1");
    for (int i = 0; i < n; i ++) {
        for (int j = 0; j < n; j ++) {
            int provjera;
            do {
                System.out.println("Unesi element[" + i + "][" + j + "]");
                matrica[i][j] = scanner.nextInt();
                provjera - matrica[i][j];
            } while (provjera != 1 && provjera != 0);
        }
    }
    int brojPonavljanja ponavljanje(matrica);
    System.out.println(brojPonavljanja);
}
public static int ponavljanje(int[][] matrica) {
    int brojac = 0;
    int redovi = matrica.length;
    int stupci = matrica[0].length;
    for (int i = 1; i < redovi 1; i ++) {
        for (int j = 1; j < stupci 1; j ++) {
            if (matrica[i][j]0 && gore lijevo, gore, gore desno, lijevo, desno, dolje lijevo, dolje, dolje desno matrica[i - 1][j matrica[i][j - 1] matrica[i + 1][j brojac ++;
                    1] == 1 && matrica[i - 1][j]1 && matrica[i - 1][j + 1]1 && matrica[i][j + 1] == 1 && == == 1 && - 1] == 1 && matrica[i + 1][j] == 1 && matrica[i + 1][j + 1] == 1) {}
        }
        return brojac;
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>Potrebno je napisati program u Javi koji će za svaku kvadratnu matricu pokrenuti N niti * (jedan red matrice = jedna nit). Svaka nit bi trebala imati dodijeljeno ime u obliku "Nit 0; Nit 1; Nit 2 itd..." te bi trebala irzačunati sumu dodijeljenog reda * matrice i ispisati je u obliku npr. "Nit 0 suma=22". Napomena - niti se trebaju izvršavati u redoslijedu kako su pokrenute.</strong></summary>
	
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System. in);
        System.out.println("Unesi n:");
        int n = scanner.nextInt();
        int[][] matrica = new int[n][n];
        for (int i = 0; i < n; i ++) {
            for (int j = 0; j < n; j ++) {
                System.out.println("Unesi element matrice");
                matrica[i][j] = scanner.nextInt();
            }
        }
        for (int i = 0; i < n; i ++) {
            Thread nit = new Nit(matrica, i);
            nit.start();
        }
        scanner.close();
    }
}


public class Nit extends Thread {
    private int[][] matrica;
    private int redak;
    public Nit(int[][] matrica, int redak) {
        this.matrica = matrica;
        this.redak redak;
    }
    @Override public void run() {
        int suma = 0;
        for (int stupac : matrica[redak]) {
            suma = suma + stupac;
        }
        System.out.println("Nit " + redak + "suma= " + suma);
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>TRANSPONIRANA MATRICA</strong></summary>
	
```java
import java.util.Scanner;

public class MatricaTransponirana {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System. in);
        System.out.println("Unesite broj redaka matrice: ");
        int redci = scanner.nextInt();

        System.out.println("Unesite broj stupaca matrice: ");
        int stupci = scanner.nextInt();

        int[][] matrica = new int[redci][stupci];
        System.out.println("Unesite elemente matrice:");
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                matrica[i][j] = scanner.nextInt();
            }
        }
        System.out.println("Originalna matrica:");
        ispisiMatricu(matrica, redci, stupci);

        int[][] transponiranaMatrica = new int[stupci][redci];
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                transponiranaMatrica[j][i] = matrica[i][j];
            }
        }
        System.out.println("Transponirana matrica:");
        ispisiMatricu(transponiranaMatrica, stupci, redci);
    }
    private static void ispisiMatricu(int[][] matrica, int redci, int stupci) {
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                System.out.print(matrica[i][j] + " ");
            }
            System.out.println();
        }
    }
}

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>ZMIJA</strong></summary>
	
```java 
import java.util.Scanner;

public class MatricaZmija {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System. in);
        System.out.println("Unesite broj redaka matrice: ");
        int redci = scanner.nextInt();

        System.out.println("Unesite broj stupaca matrice: ");
        int stupci = scanner.nextInt();
        int[][] matrica = new int[redci][stupci];

        System.out.println("Unesite elemente matrice:");
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                matrica[i][j] = scanner.nextInt();
            }
        }
        System.out.println("Originalna matrica:");
        ispisiMatricu(matrica, redci, stupci);

        System.out.println("Matrica u obliku zmije:");
        ispisiMatricuZmija(matrica, redci, stupci);
    }
    private static void ispisiMatricu(int[][] matrica, int redci, int stupci) {
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                System.out.print(matrica[i][j] + " ");
            }
            System.out.println();
        }
    }
    private static void ispisiMatricuZmija(int[][] matrica, int redci, int stupci) {
        for (int i = 0; i < redci; i ++) {
            if (i % 2 == 0) {
                for (int j = 0; j < stupci; j ++) {
                    System.out.print(matrica[i][j] + " ");
                }
            } else {
                for (int j = stupci - 1; j >= 0; j --) {
                    System.out.print(matrica[i][j] + " ");
                }
            }
        }
        System.out.println();
		

```
</details>

---
<br>
<br>
	
<details>
<summary><strong>SPIRALA</strong></summary>
	
```java
import java.util.Scanner;

public class MatricaSpirala {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System. in);
        System.out.println("Unesite broj redaka matrice: ");
        int redci = scanner.nextInt();

        System.out.println("Unesite broj stupaca matrice: ");
        int stupci = scanner.nextInt();
        int[][] matrica = new int[redci][stupci];

        System.out.println("Unesite elemente matrice:");
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                matrica[i][j] = scanner.nextInt();
            }
        }
        System.out.println("Originalna matrica:");
        ispisiMatricu(matrica, redci, stupci);

        System.out.println("Matrica u obliku spirale:");
        ispisiMatricuSpirala(matrica, redci, stupci);
    }
    private static void ispisiMatricu(int[][] matrica, int redci, int stupci) {
        for (int i = 0; i < redci; i ++) {
            for (int j = 0; j < stupci; j ++) {
                System.out.print(matrica[i][j] + " ");
            }
            System.out.println();
        }
    }
    private static void ispisiMatricuSpirala(int[][] matrica, int redci, int stupci) {
        int gornjaGranica = 0,
        donjaGranica = redci - 1;
        int lijevaGranica = 0,
        desnaGranica = stupci - 1;
        while (gornjaGranica <= donjaGranica && lijevaGranica <= desnaGranica) {
            for (int i = lijevaGranica; i <= desnaGranica; i ++) {
                System.out.print(matrica[gornjaGranica][i] + " ");
            }
            gornjaGranica ++;
            for (int i = gornjaGranica; i <= donjaGranica; i ++) {
                System.out.print(matrica[i][desnaGranica] + " ");
            }
            desnaGranica --;
            if (gornjaGranica <= donjaGranica) {
                for (int i = desnaGranica; i >= lijevaGranica; i --) {
                    System.out.print(matrica[donjaGranica][i] + " ");
                }
                donjaGranica --;
            }
            if (lijevaGranica <= desnaGranica) {
                for (int i = donjaGranica; i >= gornjaGranica; i --) {
                    System.out.print(matrica[i][lijevaGranica] + " ");
                }
                lijevaGranica ++;
            }
        }
        System.out.println();
    }
}

```
</details>

---
