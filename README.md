<h1>Securing Windows Server 2019 account Using GPO</h1>
<p>Securing Windows Server involves a combination of configuring settings, applying best practices, and implementing tools and technologies to protect against various threats. This project is going to cover some security implementations </p>

<h2>*Prerequisites</h2>
<p>- Windows Server 2019 with Active Directory Domain Services (ADDS)</p>
<p>- Member server 1 (MS1) with DHCP installed and running</p>
<p>- Windows 10 or 11</p>
<p>- VMs are already joined to the Domain Controller</p>

<br>

<h3>*Summary of the Steps</h3>
<p> - Create and Configure a GPO</p>
<p> - Link the GPO</p>
<p> - Test all the Policies</p>

<br>

<h3>*Restrict Logon Access - Deny log on through Remote Desktop Services</h3>
<p>1. To start securing Windows server 2019 using GPO, first we need to create a GPO in this domain to that effect. To create a GPO, from the server manager -dashboard, click on Tool and go to Group Policy Management.</p>
<p align="center"><img src="https://i.imgur.com/iyTMety.png" height="50%" width="50%" alt="image"/>

<p>2. From the Group Policy management page, right-click on Group Policy Object and click on New</p>
<p align="center"><img src="https://i.imgur.com/z5UKvzO.png" height="50%" width="50%" alt="image"/>

<p>3. This opens open a New GPO screen, input a descriptive name. We can name it: "Enhanced Security Policy-Account"</p>
<p align="center"><img src="https://i.imgur.com/axSiANO.png" height="50%" width="50%" alt="image"/>

<h3>Now Apply the following three policies to secure windows server 2019 using GPO</h3>
<h3>*Deny log on through Remote Desktop Services</h3>
<p>1. Right-click on the newly created GPO and click on Edit</p>
<p align="center"><img src="https://i.imgur.com/3LEEdHS.png" height="50%" width="50%" alt="image"/>

<p>2. On the Group Policy Management Editor page, go to this path; <b><i> Computer Configuration → Policies → Windows Settings → Security Settings → Local Policies → User Rights Assignment</i></b>.</p>
<p align="center"><img src="https://i.imgur.com/UXoWup1.png" height="50%" width="50%" alt="image"/>

<p>3. On the right pane, you can see the list of policies available, double click on “Deny log on through Remote Desktop Services” to configure it</p>
<p align="center"><img src="https://i.imgur.com/UMkIa00.png" height="50%" width="50%" alt="image"/>

<p>4. On the Deny Log on through Remote Desktop Services Properties page, check the Define the Policy Settings box, then click Add User or Group. This opens up Add User or Group page, click Browse</p>
<p align="center"><img src="https://i.imgur.com/FlCnCLB.png" height="50%" width="50%" alt="image"/>

<p>5. On the Select Users, Computers, Service Accounts or Group page, input the account’s object names, click Check names to confirm, then click OK</p>
<p align="center"><img src="https://i.imgur.com/5SYIhzi.png" height="50%" width="50%" alt="image"/>

<p>6. On the Deny Log on through Remote Desktop Services Properties page, the accounts are showing, click Apply, then OK</p>
<p align="center"><img src="https://i.imgur.com/3HpfLun.png" height="50%" width="50%" alt="image"/>

<p>7. Back on the Group Policy Management Editor page, you can see the “Deny Log on through Remote Desktop Services” is now configured and the accounts configured with it are shown too.</p>
<p align="center"><img src="https://i.imgur.com/Tqk521k.png" height="50%" width="50%" alt="image"/>

<br>

<h3>*Restrict Logon Access - Allow log on locally</h3>
<p>1. Whilst on the Group Policy Policy Editor, on the right pane, go through the list of policy available, double click on “Allow Log on locally” to configure it</p>
<p align="center"><img src="https://i.imgur.com/jfGvN0m.png" height="50%" width="50%" alt="image"/>

<p>2. Followed the steps above(used for Deny log on through Remote Desktop Services> to configure this policy. For this, I only added the administators. Then Back on the Group Policy Management Editor page, you can see the “Allow logon locally” is now configured and the accounts(Administrators) configured with it are shown too</p>
<p align="center"><img src="https://i.imgur.com/zpM1wSm.png" height="50%" width="50%" alt="image"/>

<br>

<h3>*Password Policies</h3>
<p>Password policies are rules that define requirements for creating, managing, and securing passwords, such as length, complexity, and expiration, to protect against unauthorized access.</p>
<p>1. Assuming you already right-clicked on the GPO, clicked on Edit and this has opened up the Group Policy Management Editor page. Go to this path to configure the password policy; <b><i> Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy</i></b>. And on the right pane, where the list of policy setting are listed, double-click policy you intend to edit</p>
<p align="center"><img src="https://i.imgur.com/VExtawp.png" height="50%" width="50%" alt="image"/>

<p>2. For this project, we are editing the Minimum Password length. While on the properties’ page, click define this policy, set the number of characters, click Apply then OK</p>
<p align="center"><img src="https://i.imgur.com/0PohGMm.png" height="50%" width="50%" alt="image"/>

<p>3. Back on the Group Policy Management Editor page, you can see the selected policy setting is now configured</p>
<p align="center"><img src="https://i.imgur.com/yRGxsKZ.png" height="50%" width="50%" alt="image"/>

<br>

<h3>*Audit Policies</h3>
<p>Audit policies are settings that define which events, such as login attempts or file accesses, are logged and monitored to track user activity and ensure security compliance</p>
<p>1. Assuming you already right-clicked on the GPO, clicked on Edit and this has opened up the Group Policy Management Editor page. Go to this path to configure the password policy; <b><i> Computer Configuration → Policies → Windows Settings → Security Settings → Advanced Audit Policy Configuration → Audit Policies → Logon/Logoff→ Audit Logon. Then double-click on Audit Logon to open it</i></b>.
<p align="center"><img src="https://i.imgur.com/WzfDhVh.png" height="50%" width="50%" alt="image"/>

<p>2. On the Audit Logon properties’ page, click the Configure the following audit events, then select success and failure. After this is done, click Apply then OK</p>
<p align="center"><img src="https://i.imgur.com/8D4OA4L.png" height="50%" width="50%" alt="image"/>

<p>3. Back on the Group Policy Management Editor’s page, one can see the Audit Logon is now configured(Success and failure).</p>
<p align="center"><img src="https://i.imgur.com/HkRjyHn.png" height="50%" width="50%" alt="image"/>

<br>

<h3>*Link the GPO</h3>
<p>1. </p>





<p align="center"><img src="" height="50%" width="50%" alt="image"/>
