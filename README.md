public class NumberGuess2 {
	private int yourNumber = 0;
	private String myGuessS;
	private int guesses = 0;
	private String yourNumberS;

	public void start() {
		yourNumber = (int) (Math.random() * 1000) + 1;
		guesses = 0;
		yourNumberS = convertToBinary(yourNumber);
		compareBinary();
		guessedAnswer();
	}

	public String convertToBinary(int x) {
		String s = Integer.toBinaryString(x);
		return s;
	}

	public int convertToInt(String s) {
		int y = Integer.parseInt(s);
		return y;
	}

	public void compareBinary() {
		StringBuilder sb = new StringBuilder();
		for (int y = 0; y < yourNumberS.length(); y++) {
			guess();
			if (yourNumberS.charAt(y) == '0') {
				sb.append('0');
			} else {
				sb.append('1');
			}
		}
		myGuessS = sb.toString();
	}

	public void guessedAnswer() {
		int myGuess = convertToInt(myGuessS);
		yourNumber = convertToInt(convertToBinary(yourNumber));
		if (yourNumber == myGuess) {
			System.out.println("You thought of: " + yourNumber
					+ ", I guessed it in: " + guesses + " guesses!");
		} else {
			System.out.println("You thought of: " + yourNumber
					+ ", I guessed: " + myGuess);
		}
	}

	public void guess() {
		guesses++;
	}

	public int getGuesses() {
		return guesses;
	}
}
