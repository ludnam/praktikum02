# praktikum02

package se1c2;


public class FourOutOfSixCoins {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
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

	}

}
