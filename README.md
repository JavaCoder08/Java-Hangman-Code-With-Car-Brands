package com.company;

import java.util.Scanner;


class Hangman {

   private static final String[] words = {                                                                                                                                                                                                                                                        "acura","ford","maserati","alfa romeo","f1","mazda","ariel","formula e","mclaren","aston martin","hennessey","mercedes benz","audi","holden","nissan","bmw","honda","pagani","bentley","hyundai","porsche","brabham","jaguar","renault","bugatti","ktm","srt","cadillac","koenigsegg","shelby","caterham","lamborghini","spada","chevrolet","lancia","toyota","dodge","lexus","volkswagen","ferrari","lotus"};
   private static final String word = words[(int) (Math.random() * words.length)];
   private static String asterisk = new String(new char[word.length()]).replace("\0", "_");
   private static int count = 0;

   public static void main(String[] args) {
       Scanner sc = new Scanner(System.in);

       while (count < 12 && asterisk.contains("_")) {
           System.out.println("Guess any letter in the word");
           System.out.println(asterisk);
           String guess = sc.next();
           hang(guess);
       }
       sc.close();
   }

   public static void hang(String guess) {
       StringBuilder newasterisk = new StringBuilder();
       for (int i = 0; i < word.length(); i++) {
           if (word.charAt(i) == guess.charAt(0)) {
               newasterisk.append(guess.charAt(0));
           } else if (asterisk.charAt(i) != '_') {
               newasterisk.append(word.charAt(i));
           } else {
               newasterisk.append("_");
           }
       }

       if (asterisk.equals(newasterisk.toString())) {
           count++;
           hangmanImage();
       } else {
           asterisk = newasterisk.toString();
       }
       if (asterisk.equals(word)) {
           System.out.println("Correct! You win! The word was " + word);
       }
   }

   public static void hangmanImage() {
       if (count == 1) {
           System.out.println("Wrong guess, try again");
           System.out.println();
           System.out.println();
           System.out.println();
           System.out.println();
           System.out.println("______");
           System.out.println();
       }
       if (count == 2) {
           System.out.println("Wrong guess, try again");
           System.out.println();
           System.out.println();
           System.out.println();
           System.out.println();
           System.out.println("___|___");
           System.out.println();
       }
       if (count == 3) {
           System.out.println("Wrong guess, try again");
           System.out.println("    ");
           System.out.println("    ");
           System.out.println("    ");
           System.out.println("    ");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("___|___");
       }
       if (count == 4) {
           System.out.println("Wrong guess, try again");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("   |");
           System.out.println("___|___");
