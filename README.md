# fork-testing

## Purpose

Even though students applied for the loan and were accepted, HELSB doesn't have enough information about the students to form a legally binding contract to guarantee the students pay back the loan. That is why more information like the student's next of kin, home address, and other details need to be collected through the screening process.

This form service aims to make the gathering of these details more efficient, by making it more convenient for the students to provide these details to HELSB.

 #note However, this is just a prototype of the model, so it has limited functionalities compared to a full scale implementation of the system.

## Client Side

*This is what is presented to the students.*

### Pages

1 - **Proof Of Payment:** Every student whether returning or first year, must pay for the screening form. After paying for the form, by whatever method, they are provided with a transaction ID, or in other words a receipt number. This is used as proof of payment on the first page

   If you are a returning student, you are asked to give extra information e.g. Student Loan Number from previous year's screening. Also serves as a proof of identity for returning students.

2 - **Login**

- Enter Receipt Number of purchased form
- Checkbox for whether the student is a returning student or not.
- If they are applying for the first time, they only have to enter the receipt number.  
- Returning students have to provide more information as proof of identity.
- #note After someone applies, the receipt is removed from the database, to avoid someone trying to use the same receipt as proof of payment.

3 - **First Year Student form**

- The actual contract to be filled in between the Student and the Loans Board
- Complete details of the form are in the `bc.md` file on the GitHub page
- On submission, Loan number is automatically generated, and added to the Student's record together with the other details to be sent to the database.
- After the form has been submitted successfully, their student record is created in the database with the given details. They are then redirected to the Login page.
- The Loan Number is then displayed to them, with a note to the user to keep it somewhere safe.

4 - **Returning Student form**

- The contract to be filled in between the Student and the Loans Board.
- Complete details of the form are in the `bc2.md` file on the GitHub page
- When the user authenticates with the receipt and student loan number, the loan number is used to fetch a student record with the matching loan number. The user is then returned, and their details automatically filled into the form on the Frontend.
- #note Not all Fields should be open to updates, for example it wouldn't make sense for someone to change their name every time they screen. Only fields for the bank details and the guardian details are left open for changer.

### After Form Submission

- The student is then redirected to the Login Page, and a message will be displayed that the form submission was successful. If a first year form is what was submitted, the new Student Loan number is displayed to the student, and they are prompted to keep it somewhere safe.

## Admin Dashboard

*This is what is presented to the Loans Board.*

It would be a dashboard that shows all the details of the students who managed to screen. The Files that they uploaded for further confirmation e.g. Results and Acceptance letters etc. are also shown and can be downloaded and viewed by the admin. After careful review, the admin can confirm the student.
If, for example, a student uploaded improper/invalid files, the admin will not confirm them and instead send them an email for example to notify them of what problem they found with their files, and prompt them to do the screening process again.
