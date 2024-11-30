
import 'dart:io';

void main() {
  // Collect Student Information
  stdout.write("Enter the student's name: ");
  String? studentName = stdin.readLineSync();

  // Validate student's name
  if (studentName == null || studentName.trim().isEmpty) {
    print("Invalid name. Please restart the program and provide a valid name.");
    return;
  }

  // Input Subject Scores
  double mathScore = getScore("Math");
  double scienceScore = getScore("Science");
  double englishScore = getScore("English");

  // Calculate Total and Average Scores
  double totalScore = mathScore + scienceScore + englishScore;
  double averageScore = totalScore / 3;

  // Assign Grade
  String grade;
  String rating;
  if (averageScore >= 90) {
    grade = "A";
    rating = "Excellent";
  } else if (averageScore >= 80) {
    grade = "B";
    rating = "Very Good";
  } else if (averageScore >= 70) {
    grade = "C";
    rating = "Good";
  } else if (averageScore >= 60) {
    grade = "D";
    rating = "Accepted";
  } else {
    grade = "F";
    rating = "Failed";
  }

  // Display Results
  print("\n--- Student Report ---");
  print("Name         : $studentName");
  print("Math         : $mathScore");
  print("Science      : $scienceScore");
  print("English      : $englishScore");
  print("Total Score  : $totalScore");
  print("Average Score: ${averageScore.toStringAsFixed(2)}");
  print("Grade        : $grade");
  print("Rating       : $rating");
  print("----------------------");
}

// Function to get a valid score for a subject using if-else
double getScore(String subject) {
  while (true) {
    stdout.write("Enter $subject score (0-100): ");
    String? input = stdin.readLineSync();

    if (input == null || input.isEmpty) {
      print("Input cannot be empty. Please enter a valid number.");
    } else if (double.tryParse(input) == null) {
      print("Invalid input. Please enter a valid number.");
    } else {
      double score = double.parse(input);
      if (score < 0 || score > 100) {
        print("Invalid score. Please enter a number between 0 and 100.");
      } else {
        return score; // Valid score
      }
    }
  }
}
