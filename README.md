Download Link: https://assignmentchef.com/product/solved-cse-465-assignment-2-implementing-an-rbac-engine
<br>
<ol>

 <li><strong> Implementing an RBAC Engine (100 Points). </strong></li>

</ol>

For this assignment, you will implement an RBAC Engine as it was depicted in class. Your engine should be able to load a syntactically-correct RBAC policy, that is, it should be able to parse the policy from a text file, store the policy within some internal data structures, and been able to respond to an authorization request asking if a given user can be granted or denied a given permission. In addition, your engine should allow for modifying the loaded policy by adding or removing permissions, users and roles, and by changing the <em>role-assignment </em>(RA), <em>permission-assignment</em> (PA) and the <em>role-hierarchy</em> (RH) relations as discussed in class.




You are free to implement your RBAC engine using the programming language of your choice. However, <strong>you are required to</strong> <strong>implement the command line interface</strong> we discuss next, so we can properly test your engine and we can correctly award you all the points you will deserve for your hard work. Please be advised that any deviations from the expected behavior of your code, e.g., it fails to compile or implement this command line interface correctly, will result in valuable points being deducted from your final assignment grade.




Overall, the following commands must be supported:







<h3>load-policy policy-file-name</h3>




Parses a text file identified by <em>policy-file-name</em>, containing an RBAC policy in the format shown in the class slides, and loads it into the internal data structures implemented by your engine. You should be able to load any policy that implements such a format, and <strong>you can expect all policies to be syntactically correct</strong>, that is, there is no need to implement an advanced parser that can detect and react to formatting issues within <em>policy-file-name</em>. If a given policy has syntax errors, you can just abort execution gracefully. In case the command succeeds or fails, <strong>no message must be shown to the screen</strong>.




show-policy




Displays an already-loaded policy into the screen. For simplicity, you can use the same format as shown in class, or implement your own. If no policy has been loaded beforehand, no output will be produced by your engine. Since this is just an auxiliary command, there is no need for the format displayed by this command to match exactly the one contained in a text file containing the RBAC policy that was loaded beforehand.




<h3>check-permissionuser-name permission-name</h3>




Checks if the permission identified by <em>permission-name</em>, can be granted to the user identified by <em>user-name</em>. If the permission can be granted, a message of the form: Permission Granted! should be outputted to the screen. Otherwise, the message Permission Denied! should be shown. Both messages should terminate with a carriage return (
). No need to include any extra information in your response message.




<h3>add-user user-name</h3>




Adds a user identified by <em>user-name</em> to a previously-loaded policy. In case the command succeeds, or in case the command fails, e.g., no policy has been loaded, or <em>user-name</em> is already defined in the policy, <strong>no message must be shown to the screen</strong>.




remove-user <em>user-name</em>




Removes a user identified by <em>user-name</em> to a previously-loaded policy. In case the command succeeds, or in case the command fails, e.g., no policy has been loaded, or <em>user-name</em> was not listed in the policy, <strong>no message must be shown to the screen</strong>.










<h3>add-rolerole-name</h3>




Adds a role identified by <em>role-name</em> to a previously-loaded policy. In case the command succeeds, or in case the command fails, e.g., no policy has been loaded, or <em>role-name</em> is already defined in the policy, <strong>no message must be shown to the screen</strong>.




remove-role <em>role-name</em>




Removes a role identified by <em>role-name</em> to a previously-loaded policy. In case the command succeeds, or in case the command fails, e.g., no policy has been loaded, or <em>role-name</em> was not defined in the policy, <strong>no message must be shown to the screen</strong>.




<h3>add-permissionpermission-name</h3>




Adds a permission identified by <em>permission-name</em> to a previously-loaded policy. In case the command succeeds, or in case the command fails, e.g., no policy has been loaded, or <em>permission-name</em> is already defined in the policy, <strong>no message must be shown to the screen</strong>.




remove-permission <em>permission-name</em>




Removes a permission identified by <em>permission-name</em> to a previously-loaded policy. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.




<h3>add-permission-to-rolepermission-name role-name</h3>




Assigns the permission identified by <em>permission-name</em> to the role identified by <em>role-name</em>, thus modifying the PA relation consequently. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.




remove-permission-from-role <em>permission-name role-name</em>




Removes the assignment of the permission identified by <em>permission-name</em> to the role identified by <em>role-name</em>, thus modifying the PA relation consequently. In case the command succeeds, or in case it fails, e.g., <em>permission-name</em> and <em>role-name</em> were not related, or one of the two is missing in the policy, <strong>no message must be shown to the screen</strong>.




<h3>add-role-to-userrole-name user-name</h3>




Assigns the role identified by <em>role-name</em> to the user identified by <em>user-name</em>, thus modifying the RA relation consequently. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.




remove-role-from-user <em>role-name user-name</em>




Removes the assignment of the role identified by <em>role-name</em> to the user identified by <em>user-name</em>, thus modifying the RA relation consequently. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.







<h3>add-senior-rolesenior-role-name junior-role-name</h3>




Adds the role identified by <em>senior-role-name</em> as a senior role of the role identified by <em>junior-role-name</em>, thus modifying the RH as a consequence. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.







<h3>remove-senior-rolesenior-role-name junior-role-name</h3>




Removes the role identified by <em>senior-role-name</em> as a senior role of the role identified by <em>junior-role-name</em>, thus modifying the RH as a consequence. As with all previous commands, the command should return quietly, that is, <strong>no message must be outputted to the screen</strong> if it succeeds or fails.










<strong>Sample Command Line Execution </strong>




The aforementioned commands will be executed in sequence, separated by a semicolon, producing a single output to the screen as a result of invoking the checkpermission command at the end. In the following example, a policy called ExampleASU.txt, similar to the one listed in the class slides, is first loaded, and a permission on a user called “Josie” is checked next. Once a response message is shown to the screen, your engine should terminate quietly. You are expected to parse the sequence of commands, separate each command, and execute it subsequently. Also, you should make sure your RBAC Engine can be called by the rbacmonitor name in the command line, by properly customizing the sample make file that will be provided in the class Blackboard site.




&gt; rbacmonitor “load-policy Example-ASU.txt; check-permission Josie p1”

Permission DENIED!




In another example, the sample Example-ASU.txt policy is first loaded, a permission is added to the <em>Student</em> role, and then the same permission is checked for the user “Josie”. The result of executing the command differs from the previous example as a resulting of adding a new permission to the <em>Student</em> role.




&gt; rbacmonitor “load-policy Example-ASU.txt; add-permission-to-

role p1 Student; check-permission Josie p1” Permission GRANTED!





