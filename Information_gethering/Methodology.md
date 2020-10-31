### 6 Phases of recon
1.scope domine
2.acquistions
3.ASN enumeration
4.revers whois
5.subdomin enumeration
6.port analysis

	scope domine
1.find root /seed
	to find what all the domine are in scope in bug bounty
	this is simple and first step
	
2.acquistions
	we need to gether seed /root .acquistions are new way to expand our avilable asserts if they are in scope .we can investigate company acqusitions on sits like https://crunchbase.com,
	wikipedia, google you can search google like acquisitions made by mazzady
	
3.ASN enumeration
	asn is autonomous system number asn is allocated to each as for use in bgp routing
	 ASN uniquely identifies each network on the Internet.
	 you can find asn in the site like https://bgp.he.net you can also use cmd line asn enumeration 
	 using metabigor and asn lookup by yassine 
	 To find more seed domins we need to scan whole asn with port scaner and return any root domins we see in ssl certificates ,etc
	 $amass intel -asn 4657
	
4.reverse whois
	every website as register info about the page two key picess of data we can use are organisation name and email in whoixy lookup
	you can access this by whoxy.com
	you can also automate this throw domlink.py -d mazzady.com -o mazzady_output.txt
	$python3 domLink.py  -A 57f575fad6f96ab6w315cbaecae138247 -o mazzady.txt mazzady.com
	a.) ad/anlaytics relationships
		you can also gleen related domins and subdomin by looking at the target ad/anlaytics relationships coder many websites uses the same coder across the domin. we can look at the relationship with buildwith.com
	b.)google dorks
		site:twitch.tv -www.twitch.tv -dev.twitch.tv until you find all subdomain
	c.) shadon
		https://www.shodan.io/search?query=mazzady.com
	
5.subdomin enumeration
	Are divided into three 
	a.) linked and js Discovery 
	b.) subdomin scraping 
	c.) subdomin bruteforce
	
	1. linked and js discovery
	another way to examine all the link in main target using burpsuite pro
	we can visit a seed/root and reqursively spider all the links and their link and so on until we have found all sites could be in scoup 
	you can also use gospider and hakrawler in cmd
	
	2.subdomain enumeration with subdoaminizer
	  subscraper
	  find subdomain referenced in js file 
	  find cloud services references in js file 
	  use the shannon entropy formula to find potentialy sensitive file in js
	  $ python3 SubDomainizer.py  -u https://yeswehack.com
	
	3.subdomain scraping sources 
	subfinder -d yeswehack.com -v
	image as been attached 
	amass and subfinder and git-subdomain.py for subdomain scraping	
	amass -d twitch.tv
	subdomain with cloud ranges
	you can use sslscrape or you can creat by our own by Daehee park outliness it here.

	4.subdoamin brutforcing amass
	amass offer by enum tool using the brute switch
	~$ amass enum  -brute -d twitch.tv -src
	its build in list but can specify you own list
	you can also specipy any number of resolves 
	~$ amass enum -brute -d twitch.tv  -rf  resolves.txt  -w bruteforces.list

	same thing can be done in shuffledns
	~$ shuffledns -d hackerone.com -w worldlist.txt  -r resolvers-excellent.txt
	this all things become super cool when you use good word list 
	go see for what where when who worldlist by tomnom

	5.alteration scanning altdms
	now amass as logic to check for these permition amass includes in defult pip install -r requirements.txt

other 
	after findings this go for port scan using mass can 
	most hacker could use nmap  here but masscan is more faster for general finding open port tcp 
	simple syntax  for scanning for list of ips:
	$host twitch.tv
	$masscan -p1-65535-iL 127.0.0.1 --max-rate1800 -oG $outputfile 

	port analysisa(dnmasscan)
	one limitation of masscan is that it only scan ip address. Y
	dnmasscan example.txt dns.log-p80,443,8080 -oG masscan.log

	service scanning (brutespry)
	when we get service port  information we can feed it to nmap to get oG output file 
	we can scan remote administration protocalsfor defult passwords with tools called brutespry

	github dorking
	many orgenaization grow in there engineer tearms soner or later new devloper
	or they are stap will leap sources code online throw public github.com
	"github search" 
	github sensitive data exposure @the3g3ntelmans.

	screenshot (eyewitness,aquatone, httpscreenshot)
	you can do this step  manualy or by taking 10 targets at the time or you can  take screenshot 

subdomain takeover(can i take over xyz)
	if subdomain pointing to github.com and the user decided to delet the page now the the attacker can creat the page and creat and  add the cname containing files 
	A Great resouces for subdomain takeover is ED 	overlows repo can i take over xyz
	SUBOVER & NUCLEI
Automation ++ 
	interlace

Framework 
S-tires automation writing their own moduel has GUI run interativily mange data via bd scale across multiple boxes.Send alert to users. uses novel techniques and iterates quicly.ML+AI
