**CYBERKILL CHAIN**



**Inspired by the military kill chains, the Cyber Kill Chain is a cyber security framework introduced by Lockheed Martin in 2011. It is created to help organisations defend against cyber attacks by understanding how they are conducted. The Cyber Kill Chain divides an attack into seven stages:**



**Reconnaissance: In the first stage, the attacker gathers information about the target**



**Weaponisation: Once proper reconnaissance is conducted, the attacker creates a deliverable payload or modifies an existing one based on the target system’s vulnerabilities**



**Delivery: Once ready, the attacker sends the weaponised payload to the target**



**Exploitation: Once executed, the payload exploits a vulnerability in the target’s system**



**Installation: The exploitation enables the attacker to install a backdoor or malware to maintain persistence in the target’s environment**



**Command \& Control (C2): Using the installed backdoor, the attacker can control the compromised system**



**Actions on Objectives: Reaching this far, the attacker can now carry out further actions such as data exfiltration or other systems’ exploitation**



**When an organisation learns about each stage, it has a better chance of breaking the chain and interrupting an attack while it is in progress.**



**Reconnaissance has its origins in the military and refers to the act of gathering information about a target. In cyber security, this stage collects information about the target’s vulnerabilities and weaknesses to discover potential entry points.**



**Reconnaissance can be divided into two types: passive and active. When carrying out passive reconnaissance, the attacker performs their activities without making any “noise,” for example, using open-source intelligence (OSINT). However, in the case of active reconnaissance, the attacker cannot remain completely quiet and invisible; it requires some form of interaction with the target organisation, such as using social engineering against the target’s personnel or scanning a target system for vulnerabilities.**



**Defence tactics include minimising public information exposure. This countermeasure is achieved by limiting the information on websites, social media accounts, and DNS records. Furthermore, the WHOIS records should not reveal any names or addresses that are best left private; many registrars offer a privacy service, usually for an added cost.**



**Monitoring and analysing network traffic and logs is a must to detect vulnerabilities and network port scans. The security team must monitor the network traffic actively to detect scanning traffic. Checking the service logs is also necessary to uncover reconnaissance attempts.**



**Once enough information has been gathered about the target, the attacker proceeds to the next stage, weaponisation. Based on the information the attacker has gathered about the target systems, they can create a payload tailored to exploit the discovered weaknesses. The attacker might use a ready-made exploit, edit an existing one, or create one from scratch. We should note that various frameworks and toolkits can help them in this stage.**



**Many attackers resort to the use of obfuscation or encryption to evade detection. Furthermore, they might hide it in an innocuous-looking file, such as an MS Word or a PDF file. The critical thing to note is that at the end of this stage, a deliverable malicious file will be ready to be delivered to the target system.**



**Attackers might use one of the available exploit kits. An exploit kit is an automated platform containing various exploits for various vulnerabilities. These platforms make it easy for attackers to package the exploit code within a payload, such as an executable file or specific documents.**

**Once the malicious file is ready, the attacker might craft a phishing email with a malicious attachment, set up a web page to host it or save it on a USB memory drive. On the other hand, if the attacker wants to target a vulnerable service, the attacker needs to plan how to deliver the payload to the vulnerable service in the next phase.**

**Countermeasures Against Weaponisation: Examples**

**On the defender’s side, user training is indispensable. When a user receives an email, they need to be careful if it contains any attachments; moreover, they should know how to inspect the email source to check its legitimacy. Furthermore, if the email includes an encrypted zip file of the payload and the decryption password, the user should suspect such email instructions before rushing to satisfy their curiosity. User cyber security training is a continuous process and an indispensable piece of any solid defence.**



**In addition to user training, it is reasonable to disable any unnecessary features, uninstall unnecessary software, and remove unnecessary browser plugins. It is crucial to restrict potentially risky features, such as disabling macros in Office documents or limiting them to signed and trusted sources. Such policies can be enforced via Windows group policy, which helps reduce the potential attack surface.**



**Attackers keep getting creative for the successful delivery of their exploit payload.**



**Phishing emails: These emails usually contain malicious attachments but might use links to malicious downloads. File names play a significant role in this attack; invoice.pdf.exe might trick the target user, unlike program.exe.**

**Spear phishing emails refer to a targeted attack where the emails are crafted to resemble legitimate communication from a source known or trusted by the recipient. For example, the sender’s name and email address are spoofed to appear as the recipient’s manager.**

**Malicious web links: The attacker might host the exploit kits on public websites. Domain spoofing and URL shortening are also used to make the links appear less suspicious.**

**File-sharing platforms: Attackers might upload malicious files to file-sharing web services, relying on people’s familiarity with the providers.**

**Malvertising: The attackers show advertisements on legitimate websites to redirect users to the malicious page.**

**SMS Phishing (Smishing): The attacker sends text messages with malicious links or instructions to download malware.**

**Social engineering: The attacker might convince an unsuspecting user to download and run a malicious program.**

**Physical means of delivery: The malicious code might be saved on a USB flash memory and left in an accessible location. Another example is mailing an innocuous-looking DVD containing the malicious program. The attacker must always provide a convincing context, such as the DVD containing a catalogue of interest to the target personnel.**





**Countermeasures Against Delivery: Examples**

**It is like a cyber arms race where the defence team must work against every delivery method they are aware of. The list starts with user training in cyber security awareness. The users are educated about safe browsing practices, phishing, and social engineering attacks. Going beyond user training, email and web filtering are the standard in many organisations. Web application firewalls (WAFs) are indispensable in blocking malicious files available via the web. Moreover, network monitoring and patch management become increasingly vital in large corporations. Many other defence tactics exist to break the attack chain and prevent the successful delivery of the malicious payload.**





Following a successful installation of persistent access within the target environment, the attacker needs to maintain reliable and discreet access to the compromised systems so that they can later act on their objectives. The Command and Control (C2) phase aims to establish this covert communication channel for use in the next phase. In this phase, the attacker sets up the C2 communication channel between the compromised systems and their own infrastructure.



Attackers can use various techniques to create such infrastructure as domain names, IP addresses, and cloud services. To evade detection, the attacker might resort to different methods; examples include creating random domain names and frequently changing the IP address. In some cases, the attackers might use a seemingly legitimate domain so as not to raise suspicions. It is also common to use encryption, among other types of obfuscation techniques, to avoid getting discovered.



Command and Control: Examples

We will list a few tactics employed by C2 infrastructure to achieve resilient covert communication. The first tactic is using common application layer protocols such as HTTP, HTTPS, DNS, and SMTP for C2 communication, which allows blending in with legitimate traffic. Furthermore, C2 infrastructure may use encrypted channels such as HTTPS to hide from network monitoring tools. It is also possible to use DNS tunnelling, i.e., encoding data within DNS requests, to bypass various security solutions and firewalls.



Regarding domain addresses, C2 communication can use social media platforms, such as X direct messages, to send commands to a botnet. Another option is using legitimate cloud services, such as Dropbox and Google Docs, especially for data exfiltration.



If the attacker registers their own domain name and uses it to establish the C2 infrastructure, it will be too easy to take it down. Therefore, the C2 relies on various techniques to ensure resilient communications. Examples include Domain Registration Algorithms (DGAs) and Fast Flux. DGA refers to creating a vast number of domain names, for example, 50 000, using a predefined algorithm. The owner of the C2 infrastructure registers only 1% or 2%. The malware, in turn, will iterate over this extensive list till it finds an active one. If the domain gets blocked or seized, the malware switches to the next active one.



Fast Flux associates hundreds or thousands of IP addresses with a single domain name; furthermore, these IP addresses are swapped every few minutes. Compromised devices, e.g., IoT devices, act as proxies to forward traffic to the hidden C2 server. If any IP address, i.e., proxy node, gets blocked, the malware automatically switches to the following IP address.



Countermeasures against Command and Control: Examples

The cyber security team must consider various solutions to detect and disrupt C2 traffic. Let’s explore a few.



Network monitoring via firewalls, IDS, and IPS plays a significant role in detecting and blocking C2 traffic. It is essential to watch for unusual traffic patterns and volumes and connections to known malicious IP addresses.



Because DNS traffic can be used to tunnel C2 traffic, monitoring DNS traffic and analysing DNS queries is equally vital, especially when stumbling across unusually long ones or detecting high volumes of requests to suspicious domains. Moreover, because web shells use HTTP and HTTPS protocols, monitoring web traffic helps detect suspicious connections, while content filtering can block access to suspicious URLs. Furthermore, encryption inspection would be necessary to decrypt and inspect encrypted traffic to detect C2 communication using HTTPS.



Many security teams go a step further and deploy honeypots to detect and analyse C2 communication attempts and monitor attacker behaviour. The list goes on, and we leave a more detailed dive into countermeasures to other rooms.



After establishing a covert C2 communication channel, the attacker can carry out their original goals. In this phase, the attacker executes their original goals, which range from data exfiltration (information theft) to service disruption.



Actions on Objectives: Examples

The attackers might be targeting an organisation for a variety of reasons. Some attacks are blaring. For example, if the attacker is only interested in seeking damage, they can launch a destructive attack by deleting or corrupting data to disrupt normal system operations. On the other hand, attackers might be after financial gain and “quick riches”, usually by carrying out a ransomware attack. Or they might be trying to get rich more discreetly, such as financial theft via unauthorised wire transfers or other fraudulent transactions.



In a covert attack, such as industrial and political espionage, the attackers would be most interested in stealing sensitive files from their target, commonly called data exfiltration. Alternatively, if the attacker is interested in getting access to other systems on the target network, they will try to stealthily compromise other systems on the network, i.e., lateral movement.



Depending on the target organisation, the threat actor might be interested in manipulating Industrial Control Systems (ICSs). It is also equally plausible that this is preceded by establishing a long-term persistent presence so that they carry out their attack at a time of their choosing. The execution depends on the threat actor and their motives. We mentioned a few examples, but the list can get much longer.



Countermeasures Against Actions on Objectives: Examples

Let’s explore a few countermeasures that an organisation can consider. Data Loss Prevention (DLP) solutions can play a key role in preventing unauthorised data exfiltration. Furthermore, establishing a reliable backup and recovery plan is indispensable to mitigate ransomware and other destructive attacks.



To minimise the damage an attacker can cause, an organisation needs to consider network segmentation and strict access controls. Network segmentation isolates critical systems in the case of a compromised system on another segment and prevents the attacker from moving laterally; moreover, access controls and the principle of least privilege limit who can access sensitive systems and data.



User activity monitoring helps detect suspicious behaviours; for example, you would not expect your users to be sending DNS queries after midnight. On the other hand, Endpoint Detection and Response (EDR) solutions offer an excellent choice for monitoring and detecting suspicious activities on endpoints, such as processes attempting to access or modify sensitive data, encrypt files, or establish unauthorised network connections.

