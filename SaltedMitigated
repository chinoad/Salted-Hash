import javax.crypto.SecretKey;
        import javax.crypto.SecretKeyFactory;
        import javax.crypto.spec.PBEKeySpec;
        import java.security.NoSuchAlgorithmException;
        import java.security.SecureRandom;
        import java.security.spec.InvalidKeySpecException;
        import java.util.Scanner;

public class SaltedMitigated {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        System.out.println("Hello. Please enter your PIN");
        char[] inputPin = input.next().toCharArray();

        //CSPRNGs
        SecureRandom random = new SecureRandom();
        byte[] salt = new byte[20];
        random.nextBytes(salt);

        try {
            SecretKeyFactory skf = SecretKeyFactory.getInstance("PBKDF2WithHmacSHA512");
            PBEKeySpec spec = new PBEKeySpec( inputPin, salt, 5, 20 );
            SecretKey key = skf.generateSecret( spec );
            byte[] res = key.getEncoded( );
            System.out.println("Salted Hash Password is:" + res);

        } catch (NoSuchAlgorithmException | InvalidKeySpecException e){
            throw new RuntimeException(e);
        }

    }

}
