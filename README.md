# SayiTahminOyunu

import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Random rand = new Random();
        int number = rand.nextInt(100);

        Scanner input = new Scanner(System.in);
        int right =0;
        int selected;
        int [] wrong =new int[5];
        boolean isWin = false;
        boolean isWrong = false;

        while (right<5){
            System.out.println("Lütfen tahmininizi giriniz:  ");
            selected = input.nextInt();

            if (selected<0 || selected>99){
                System.out.println("Lütfen 0-100 arası bir sayı giriniz!");

                if (!isWrong){
                    isWrong =true;
                    System.out.println("Bir daha hatalı giriş yaptığınızda hakkınızdan düşecektir!");
                }else{
                    right++;

                    System.out.println("Çok fazla hatalı giriş yaptınız! Kalan hakkınız:  " + (5-right));
                }
                continue;
            }

            if (selected==number){
                System.out.println("Tebrikler ! doğru tahmin..Tahmin ettiğiniz sayı: "+ number);
                isWin =true;
                break;

            }else{
                wrong[right]=selected;

                right++;

                System.out.println("Hatalı sayı girdiniz!");
                if (selected>number){
                    System.out.println(selected + "  sayısı, gizli sayıdan büyüktür.");

                }else{
                    System.out.println(selected + "   sayısı, gizli sayıdan küçüktür.");

                }
                System.out.println("Kalan hakkınız: " + (5-right));
            }

        }
        if (!isWin==true && !isWrong){
            System.out.println("Kaybettiniz!!");
            System.out.println("Tahmin ettiğiniz değerler:   " + Arrays.toString(wrong));
        }

    }
}
