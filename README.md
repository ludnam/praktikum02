# praktikum02

package se1c2;

import java.util.Iterator;

public class FourOutOfSixCoins {
	
	public static int[][] combinationen = new int[15][4];

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		
		
		pruefeKombination(combinationen);
		
		for (int i = 0; i < combinationen.length; i++) {
			System.out.print("[");
			for (int k = 0; k < 4; k++) {
				
				System.out.print(combinationen[i][k] + ",");
				
			}
			System.out.print("\b]\n");
		}
		
		System.out.println("Gesamtzahl der Kombinationen: " + anzahlKombinationen(6, 4));

	}
	

	public static void pruefeKombination(int[][] pruefeKombinationArray) {
		
		int[] muenzeVierer = new int[4];
		
		//int[][] combinationen = new int[15][4];
	
		boolean combinationVorhanden = false;
		boolean vierMalVorhanden = false;
		int vierMal = 0;
		int anzahl = 0; 

		for (int i = 0; i < pruefeKombinationArray.length; i++) {
			
			muenzeVierer = viererKombi();
			
			
			for (int j = 0; j < i; j++) {
				
				for (int k = 0; k < 4; k++) {
					
					if (combinationen[j][k] == muenzeVierer[k]) {
						
						vierMalVorhanden = true;
						vierMal ++;
						
					}
					else {
						
						vierMalVorhanden = false;
						vierMal = 0;
						
					}
					
				}
				
				if (vierMal == 4) {
					
					muenzeVierer = viererKombi();
					break;
					
				}
				else {
					
					for (int l = 0; l < 4; l++) {
						combinationen[i][l] = muenzeVierer[l];
					}
					
				}
			}
			
			anzahl = i;
			
		}
		
		System.out.println("Gesamtzahl der Kombinationen: " + anzahl+1);
			
	}

	
	public static int[] viererKombi() {
	
		int zufallszahl;
		int[] muenze = new int[4];
		int[][] combinationen = new int[15][4];
		
		boolean zahlVorhanden = false;
		
		int minWert = 1, maxWert = 6, bereich = maxWert - minWert + 1;
		
		
		
		for (int i = 0; i < muenze.length; i++) {
			
			zufallszahl = (int) (Math.random()*bereich)+minWert;
			
			for (int j = 0; j < i; j++) {
				
				if (muenze[j] == zufallszahl) {
					
					zahlVorhanden = true;
					break;
					
				}
				else {
					
					zahlVorhanden = false;
					
				}
			}
			
			if(zahlVorhanden) {
				
				zufallszahl = (int) (Math.random()*bereich)+minWert;
				i--;
			}
			else {
				muenze[i] = zufallszahl;
			}
			
		}
		
		return muenze;		
	}

	public static int anzahlKombinationen(int n, int k) {

		int fakultaet_n = 1;
		int fakultaet_k = 1;
		
		for (int i = 1; i <= n; i++) {
			
			fakultaet_n = fakultaet_n*i;	
						
		}
		
		for (int j = 1; j <= k; j++) {
			
			fakultaet_k = fakultaet_k*j;	
			
		}
		
		return fakultaet_n/(fakultaet_k*(n-k));		
	}
	
}
