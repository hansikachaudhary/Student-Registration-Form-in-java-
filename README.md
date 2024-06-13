# Student-Registration-Form-in-java-
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
// Custom Exception class for invalid data entry
// Extending RuntimeException class to make a unchecked exception
class InvalidData extends RuntimeException{
 InvalidData(String message){
 super(message);
 }
}
// I have used anonymous inner class to implement ActionListener to reduce the size of code
// I have also used GridLayout to arrange components, which was not part of syllabus, 
// but I have taught in the class since layouts make arrangements easier.
class RegistrationPage{
 RegistrationPage(){
 JFrame frame = new JFrame("Registration Page");
 frame.setSize(500, 500); // Size of frame in pixels
 frame.setVisible(true);
 
frame.getContentPane().setBackground(Color.GREEN);
 
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 JLabel nlabel = new JLabel("Name: ");
 JTextField name = new JTextField();
 JPanel npanel = new JPanel(new 
GridLayout(1, 2));
 npanel.add(nlabel);
 npanel.add(name);
 JLabel rlabel = new JLabel("Roll No: ");
 JTextField roll = new JTextField();
 JPanel rpanel = new JPanel(new GridLayout(1, 2));
 rpanel.add(rlabel);
 rpanel.add(roll);
 JLabel clabel = new JLabel("CGPA: ");
 JTextField cgpa = new JTextField();
 JPanel cpanel = new JPanel(new 
GridLayout(1, 2));
 cpanel.add(clabel);
 cpanel.add(cgpa);
 JLabel blabel = new JLabel("Branch: ");
 String[] choices = {"CSE", "IT", "CSCE", 
"CSSE"};
 JComboBox<String> branch = new 
JComboBox<String>(choices);
 JPanel bpanel = new JPanel(new 
GridLayout(1, 2));
 bpanel.add(blabel);
 bpanel.add(branch);
 JLabel elabel = new JLabel("Email ID: ");
 JTextField email = new JTextField();
 JPanel epanel = new JPanel(new 
GridLayout(1, 2));
 epanel.add(elabel);
 epanel.add(email);
 JButton submit = new JButton("SUBMIT");
 JButton reset = new JButton("RESET");
 JButton ccolor = new JButton("CHANGE COLOR");
 JPanel buttons = new JPanel(new 
GridLayout(1, 3));
 buttons.add(submit);
 buttons.add(reset);
 buttons.add(ccolor);
 JTextArea tarea = new JTextArea(8, 8);
 // Adding all components to the frame
 frame.setLayout(new GridLayout(7, 1));
 frame.add(npanel);
 frame.add(rpanel);
 frame.add(cpanel);
 frame.add(bpanel);
 frame.add(epanel);
 frame.add(buttons);
 frame.add(tarea);
 // Adding event handling
 submit.addActionListener(new 
ActionListener(){
 public void actionPerformed(ActionEvent 
e){
 tarea.setText("");
 String studentName = name.getText();
 int studentRollNo = 
Integer.parseInt(roll.getText());
 float studentCGPA = 
Float.parseFloat(cgpa.getText());
 String studentBranch = 
branch.getSelectedItem().toString();
 String studentEmail = email.getText();
 // Validations
 if(roll.getText().length() <= 6 || 
roll.getText().length() >= 9)
 throw new InvalidData("Roll Number should have 7-8 digits.");
 
 if(studentCGPA < 6.0 || studentCGPA 
> 10.0)
 throw new InvalidData("CGPA should be in range 6.0 to 10.0");
 
 if(!studentEmail.matches("^[A-Za-z0-9+_.-]+@(.+)$"))
 throw new InvalidData("Email should be in valid format.");
 tarea.append("name: " + studentName 
+ "\n");
 tarea.append("Roll No.: " + 
String.valueOf(studentRollNo) + "\n");
 tarea.append("CGPA: " + 
String.valueOf(studentCGPA) + "\n");
 tarea.append("Branch: " + 
studentBranch + "\n");
 tarea.append("Email: " + 
studentEmail + "\n");
 }
 });
 reset.addActionListener(new 
ActionListener(){

 public void actionPerformed(ActionEvent 
e){
 tarea.setText("");
 name.setText("");
 roll.setText("");
 cgpa.setText("");
 email.setText("");
 }
 });
 ccolor.addActionListener(new 
ActionListener(){
 public void actionPerformed(ActionEvent 
e){
 
frame.getContentPane().setBackground(Color.PINK);
 }
 });
 }
}
class Driver{
 public static void main(String[] args){
 new RegistrationPage();
 }
}
