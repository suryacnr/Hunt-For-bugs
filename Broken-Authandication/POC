
try to change the refers : in proxy you can change its vunlerable 
eg: Refers: https://natas4.natas.labs.overthewire.org/ to http://natas5.natas.labs.overthewire.org if it changes its vunreable 

you are not loggend in try to loggin 
eg : try to change the cookie vlaue from 0 = 1
google ctf 
try to run curl -X POST https://www.mazzady.com/login  -d "username[]=surya" -d "password[]=admin"

poc 1:
1] There are two user who are part of cobalt User A and User B

2] User A has email address abc@gmail.com and

3] User B has email address xyz@gmail.com Then

4] If User A thinking to update his email to xyz@gmail.com then generally we get prompt message saying email address already taken OR email id already in used by someone.

But this is not happening here in cobalt. Hence if User A by mistakenly setting User B email address and that User B know this flow then he can reset User A Email address well this is it, Then this leads to full account takeover of all the cobalt users whose email id is @gmail.com.

poc 2:
Steps to repro:
1) Create a Phabricator account having email address "a@x.com".
2) Now Logout and ask for password reset link. Dont use the password reset link sent to your mail address.
3) Login using the same password back and update your email address to "b@x.com" and verify the same. Remove "a@x.com".
4) Now logout and use the password reset link which was mailed to "a@x.com" in step 2.
5) Password will be changed All previous password reset links should automatically expire once a user changes his email address
attacker senario
1) My email account is compromised. Attacker asks for password reset link for my Pharicator account.
2) I got to know, I change my email address on my Phabricator account. I now assume i am safe.
3) But the hacker can still use the old password reset links (which he had never used for single time) which were sent to my old email address.
4) My account is now compromised again.

poc 3 :

    First log in into the account, website will create a session for current login.
    Copy all Cookies and paste it on notepad.
    Log out your account.
    Open your chrome browser and right click on bookmark bar and add page.
    Now, on Edit Bookmark and paste it on URL and save.

javascript:void(function(){ 
    function setCookie(t) { 
    var list = t.split("; "); 
    console.log(list); 
        for (var i = list.length - 1; i >= 0; i--) { 
            var cname = list[i].split("=")[0]; var cvalue = list[i].split("=")[1]; 
            var d = new Date(); d.setTime(d.getTime() + (7*24*60*60*1000)); 
            var expires = ";domain=.wakatime.com;expires="+ d.toUTCString(); 
            document.cookie = cname + "=" + cvalue + "; " + expires; 
        } 
    } 
    function hex2a(hex) { 
        var str = ''; 
        for (var i = 0; i < hex.length; i += 2) {
            var v = parseInt(hex.substr(i, 2), 16); 
            if (v) str += String.fromCharCode(v); 
        } 
    return str; 
    } 
    var cookie = prompt("Broken Authentacation PoC", ""); 
    setCookie(cookie); 
    location.href = 'https://wakatime.com/settings/account'; 
})();

6, Click the bookmark page that you created, make sure you are in https://wakatime.com/ before you click the bookmark that you created to popup this.

Now paste your users cookies and we redirect in https://wakatime.com/settings/account

Please Watch my PoC:
Broken_Authentacation.avi (F720341)
Impact
(Session Token Not expired)

In this attack, an attacker (who can be anonymous external attacker, a user with own account who may attempt to steal data from accounts, or an insider wanting to disguise his or her actions) uses leaks or flaws in the authentication or session management functions to impersonate other users. Application functions related to authentication and session management are often not implemented correctly, allowing attackers to compromise passwords, keys, or session tokens, or to exploit other implementation flaws to assume other users’ identities.

poc 4:
misuse of auth-token
login senario
valied credintion ==> login status success &auth token recives in responces
invalied cresintion ==>  login status fail & blank auth token 

Attacker senario
 attacker submit valied credintional 
 intercepts the 1 login responces copies the auth token and drops the responces 
 send login request with target user id +wrong password 
 in responces status sets login status =success & is own  auth token value

 poc 5:
 cookie manipulation
 successfull login ==> appsets cookie 
 
 attacker senario
 attacker users login to application
 using any cookie editor replace with user id value with that of vitam of refresh page   

 poc 6:
 session invalidation
  multi login allwoed means able to login in on mobile, website and manymore &session should expriess after while but session doesnt expries for less than month 

  attacker scenario 
  try to login to multiple device 
  and reset the password now session should expre but not 
  suppose the user identify the account is compromised & change the pasword
  the active session still remains active and there was no way to invalidate the attacker sessions

 poc 7:
 account atakeover from  forget password functionality 
 forget password page gives option to select recovery option(otp/email)
 part of the option are marked as astrick(*)
 
 attacker scenario :
 attacker provides victum usr id in forget password page 
 select any recovery option & use proxy tool can modify the otp/email value in requests
 
 poc 8:
 enter forget password page and enter the email and you will get the reset password link copy that link in notpad than change the password in same browser after that logout from the website and enter the the url in the different browser and change the password if you able to change the password than there is vulnerability 
 poc 9:
 		open the same account in different browser one as victum and another as attacker if ou change the password in victum The password must also change in attacker and it should logout if the attacker still able change the name or address than there is vulnerability
poc 10:
		two factore authendication first creat two account with different name and change the settings for two factore authendication and enter the mobile number for first and secound account same mobile number first recive the otpp for two account and enter the otp for two account at the same time and logout and try to login agin if you login there is no problem if not there is vulnerability

poc 11:
      login to website page and using cookie editor copy all the cookiee to clipboard and logout and now import the cookie in cookie editor and refresh the page you can login 
      
 

poc 12:
		login to website and go to settings intercepts the request and send to reperter and logout from the website and now try to modefy the name or date of birth  if you can than sessioin doesnt expire
