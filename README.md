import java.util.*;

public class MorseCodeTranslator {
    private static final Map<Character, String> MORSE_CODE_DICT = new HashMap<>();
    private static final Map<String, Character> REVERSE_MORSE_CODE_DICT = new HashMap<>()
    static {
        String[][] morsePairs = {
            {"A", ".-"}, {"B", "-..."}, {"C", "-.-."}, {"D", "-.."}, {"E", "."},
            {"F", "..-."}, {"G", "--."}, {"H", "...."}, {"I", ".."}, {"J", ".---"},
            {"K", "-.-"}, {"L", ".-.."}, {"M", "--"}, {"N", "-."}, {"O", "---"},
            {"P", ".--."}, {"Q", "--.-"}, {"R", ".-."}, {"S", "..."}, {"T", "-"},
            {"U", "..-"}, {"V", "...-"}, {"W", ".--"}, {"X", "-..-"}, {"Y", "-.--"},
            {"Z", "--.."}, {"1", ".----"}, {"2", "..---"}, {"3", "...--"},
            {"4", "....-"}, {"5", "....."}, {"6", "-...."}, {"7", "--..."},
            {"8", "---.."}, {"9", "----."}, {"0", "-----"}, {" ", "/"}
        };
        for (String[] pair : morsePairs) {
            char letter = pair[0].charAt(0);
            String morse = pair[1];
            MORSE_CODE_DICT.put(letter, morse);
            REVERSE_MORSE_CODE_DICT.put(morse, letter);
        }
    }
    public static String textToMorse(String text) {
        StringBuilder morseCode = new StringBuilder();
        for (char c : text.toUpperCase().toCharArray()) {
            if (MORSE_CODE_DICT.containsKey(c)) {
                morseCode.append(MORSE_CODE_DICT.get(c)).append(" ");
            }
        }
        return morseCode.toString().trim();
    }
    public static String morseToText(String morse) {
        StringBuilder text = new StringBuilder();
        String[] morseWords = morse.split(" ");
        for (String code : morseWords) {
            if (REVERSE_MORSE_CODE_DICT.containsKey(code)) {
                text.append(REVERSE_MORSE_CODE_DICT.get(code));
            }
        }
        return text.toString();
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter text to convert to Morse code:");
        String inputText = scanner.nextLine();
        String morse = textToMorse(inputText);
        System.out.println("Morse Code: " + morse);

        System.out.println("Enter Morse code to convert to text (separate by spaces):");
        String inputMorse = scanner.nextLine();
        String decodedText = morseToText(inputMorse);
        System.out.println("Decoded Text: " + decodedText);
    }
}
