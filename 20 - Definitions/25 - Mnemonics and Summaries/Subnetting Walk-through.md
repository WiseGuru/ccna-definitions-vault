---
dg-publish: true
---
[[IP subnet|Subnetting]] is the practice of dividing a network into smaller subnetworks.

The CCNA *heavily* tests you on your ability to quickly understand subnets and navigate routing tables. It doesn't do this with questions like you'll find on [subnetting.org](https://subnetting.org/), but often as part of another question whose primary subject matter is something else.

To put it simply, being able to *quickly understand* the *scope of a network* with either a *dotted-decimal* or *slash-notation* network or subnet mask is the **most critical skill** needed for the CCNA. *You are not given time* to do the math of subnetting for every question, and most questions will involve subnetting in some form or another.

Below, we'll discuss what I found to be most helpful while studying and taking the test, and what you can do to get better at it.

>**NOTE**: All the examples below are for *IPv4*, because that's where it's most necessary for the CCNA. You can extend the principles to *IPv6*, but it's both a little simpler and more complicated, and it's easier to teach the differences if you already have a firm grasp of IPv4 subnetting. 

>**ALSO NOTE**: This article will focus on the practical application of subnetting, and won't go into the overarching governing ideas behind them, like [[VLSM]] or [[IPv4 Address Classes|RFC 1918]].

## IP Networks 101
In order to fully understand the following methods, you need to understand how IP addresses and network masks are composed at the bit-level.

**If you already know what I mean when I say /13 has a bit value of 8, you can click the arrow by the title of this section and skip ahead.**

>You can also go watch [Jeremy's IT Lab](https://www.youtube.com/watch?v=bQ8sdpGQu8c), which will absolutely do a better and more thorough job of explaining this. I won't be offended.

### Bits and Octets
[[IPv4]] addresses are *32-bit strings* that are *divided into four* 8-bit sections called *octets*. Addresses are read from left to right, with the left-most bits carrying higher values.
![[Subnetting Walk-through-5.png|500]]

Each *octet* can represent any number between *0* and *255*, for 256 total possible values. Each *bit* represents a *value*, and whether the bit is set to 1 or 0 indicates if the value is added to the total. The *sum total of all bits flipped to 1 are counted*

>**DISCLAIMER**: I don't think most people name the bit positions like this, but I think it's helpful. If you prefer to do *1-8* or *8-1*, that's totally fine, so long as you're consistent.

![[Subnetting Walk-through-4.png]]
You'll notice there's a pattern in the bit value; each bit is worth **2^x**, where **x** is the bit position. This will be helpful later, but for now, `write mem` this to your [[IOS Storage Locations|NVRAM]] and keep going.

Consider the following examples of octets and their bit values.
##### Example 1 - 10101010
| Bits              | 1   | 0   | 1   | 0   | 1   | 0   | 1   | 0   |
| ----------------- | --- | --- | --- | --- | --- | --- | --- | --- |
| Bit Values        | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| Octet Total Value | **128** | 128 | **160** | 160 | **168** | 168 | **170** | 170 |
128+32+8+2 = **170**

##### Example 2 - 11110000
| Bits              | 1   | 1   | 1   | 1   | 0   | 0   | 0   | 0   |
| ----------------- | --- | --- | --- | --- | --- | --- | --- | --- |
| Bit Values        | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| Octet Total Value | **128** | **192** | **224** | **240** | 240 | 240 | 240 | 240   |
128+64+32+16 = **240**

#### Composing an IP Address
When you string *four octets* together, you get an IP address.

| Octet Bits | 10101100 | 00010010 | 11110000 | 0010001 |
| ---------- | -------- | -------- | -------- | ------- |
| IP Address | 172      | 18       | 240      | 33      |

#### Bits and Octets Recap
To summarize, each *bit* has a *bit value* that is equal to **2^(bit position)**. *Octets* are composed of *8 bits*, and *four octets* make an *IPv4 address*. Onward! 

### Network Bits, Host Bits, and My First Subnet
Each IP address is composed of *two parts*; the *network bits* on the *left* and the *host bits* on the *right*. The bits in each part are [contiguous](https://www.merriam-webster.com/dictionary/contiguous); you will never have network bits and host bits intermingling.

The *network bits* define the *network*, which is the [[broadcast domain]] within which *hosts* can communicate freely. The *host bits* identify *unique addresses* on that network.

Each network has a *network address* (the first IP address in the subnet) which *identifies the network* and is used for routing purposes, and a *broadcast address* (the last IP address in the subnet) that is used to *forward packets too all other hosts* on the network. Think of the *network address* like the name of the town or neighborhood, and the *broadcast address* like the town crier or a really gossipy neighbor. All of the other addresses are known as *valid host addresses* or *valid IP addresses*, because they represent actual network endpoints.

The network bits are identified using a *network mask* (or *netmask* or *subnet mask*), which "*masks*" the *network bits* by setting each network bit to 1. *Every bit* in an IP address that is *masked by a 1* in its netmask is a *network bit*. Network masks can be written either in the long-form *dotted-decimal* format, which represents the mask with each octet's value, or the short-form *slash-notation* format, which identifies the number of network bits in the netmask. 

>I've always called all kinds of network masks **subnet masks**, regardless of context. This is probably not correct, and I may update this article later to be more correct, but right now I'm fine with it.

For example, let's look at the IP address from earlier; **172.18.240.33**, which is the *decimal* representation of the *binary* **10101100 00010010 11110000 0010001**.
##### 172.18.240.33 with a network mask of 255.255.0.0 or /16
```
10101100 00010010 11110000 0010001
11111111 11111111 00000000 0000000
```
With this netmask, the first *16* bits are masked with *1s*. This means that the remaining *16* bits (11110000 0010001) are *host bits*.
- *172.18.0.0* is the *network address*
- *172.18.0.1* - *172.18.255.254* are *valid host addresses*
- *172.18.255.255* is the *broadcast address*

##### 172.18.240.33 with a network mask of 255.255.240.0 or /20
```
10101100 00010010 11110000 0010001
11111111 11111111 11110000 0000000
```
With this subnet mask, the first *20* bits are masked with *1s*. This means that the remaining *12* bits (0000 0010001) are *host bits*.
- *172.18.240.0* is the *network address*
- *172.18.240.1* - *172.18.255.254* are *valid host addresses*
- *172.18.255.255* is the *broadcast address*. 

##### 172.18.240.33 with a network mask of 255.255.255.224 or /27
```
10101100 00010010 11110000 0010001
11111111 11111111 11111111 1110000
```
With this subnet mask, the first *27* bits are masked with *1s*. This means that the remaining *5* bits (0001) are *host bits*.
- *172.18.240.32* is the *network address*
- *172.18.240.33* - *172.18.240.62* are *valid host addresses*
- *172.18.240.63* is the *broadcast address*. 

There are **MANY** great IP calculators out there, but this one is pretty neat, as it clearly shows the binary values behind the addresses; [IP Calculator / IP Subnetting](https://jodies.de/ipcalc)

#### Network Bits, Host Bits, and My First Subnet Recap
- IP addresses are divided into two contiguous parts; **network bits** and **host bits**
	- *Network bits* define the network, or [[Broadcast domain]]
	- *Host bits* define the *unique addresses* on that network
- Each *network* has a **network address** and a **broadcast address**, and **valid host addresses**
	- *Network addresses* are the very *first address* in a network range and *identify the network*
	- *Broadcast addresses* are the very *last address* in a network range and are used to *forward packets to all hosts*
	- *Valid host addresses* or *valid addresses* are all the IP addresses in between that can be *assigned to hosts*
- **Network or Subnet Masks** literally "mask" the *network bits* in an IP address, and are commonly represented in either **dotted-decimal** or **slash notation**
	- *Dotted-decimal notation* identifies the *bit value* of the *subnet mask* of each *octet*
	- *Slash notation* identifies the *number of bits* in the *subnet mask*

### Proper Subnetting
What does it even mean "to subnet"? *Subnetting* is defined by [SolarWinds](https://en.wikipedia.org/wiki/SolarWinds#2019%E2%80%932020_supply_chain_attacks) as "the process of creating a subnetwork (also known as a subnet) within a network." [SolarWinds](https://www.bleepingcomputer.com/news/security/critical-rce-flaws-found-in-solarwinds-access-audit-solution/) also has a [pretty good IP and subnet calculator](https://www.solarwinds.com/free-tools/advanced-subnet-calculator). Thank you, [SolarWinds](https://www.bleepingcomputer.com/news/security/clop-gang-exploiting-solarwinds-serv-u-flaw-in-ransomware-attacks/), for all your hard work. 

When we're talking about *subnetting* in relation to the CCNA, we usually mean *identifying the number of valid* **hosts** *and* **networks** *given some parameters*.
This can be framed by asking you to:
- *identify network ranges*
- *divide a network into subnets to support business needs*
- *identify which network an IP address belongs to*

To do any of that, you need to be able to identify the *number of valid hosts* and the *number of subnetworks* for any given network.

#### Dividing Networks
Up to this point, we've been discussing single subnets, and that's mostly what you'll be dealing with. However, you may be asked to calculate *how many subnets can exist in a given network*.

But before we get into dividing networks, we need to talk about **Private IP Address Ranges** and ***IPv4 Address Classes***.

>**IPv4 Address Classes are (mostly) Obsolete**
	No one uses *classful networks* anymore. The only thing that's relevant about them at this point is the idea of "**Private**" vs. "**Public**" IP ranges (defined by [[IPv4 Address Classes|RFC 1918]]), and those are quite important.

![[IPv4 Address Classes#Private IPv4 Address Ranges]]

- *Public* IPv4 addresses are *publicly routable*
	- *Any device* on the internet *can connect* to *any other device* with a public IP (theoretically) by entering its IP.
	- These IP addresses are *unique* on the internet, and no two devices can have the same *public IP*
- *Private* IPv4 addresses are **NOT** *publicly routable* (big surprise)
	- Through the magic of [[NAT]], they can connect to the Internet, but they are otherwise meant for use *privately* in smaller networks
		- For example, your home computer might have *192.168.1.10*, and mine might also have *192.168.1.10*, and *that's not a problem*.

But if you open Command Prompt (or Terminal) and type in `ipconfig` (or `ifconfig`), you will notice that your home *network mask* is probably not */8 (255.0.0.0)* or */16 (255.255.0.0)*; it's probably */24 (255.255.255.0)*. This is because you're connected to a *subnet* of the *private IP range*, automatically configured by your router.

>Remember that thing I asked you to commit to memory earlier? Here's a quick reminder:
	Each bit is worth **2^x** where "**x**" is the **bit position** in the octet.

Just like how we can calculate the *bit-value of an octet*, we can **calculate the number of available networks** with *2^x*, where *x* represents the *number of non-default network* (**or subnet**) *bits*.

>What I call **non-default network bits** are called **subnet bits** by others (like [Professor Messer](https://www.professormesser.com/network-plus/n10-008/n10-008-video/calculating-ipv4-subnets-and-hosts-n10-008/)), or even just **network bits** (which is what I learned, and find confusing). I'm going to use **default network bits/default network mask** to represent the overarching network, and **non-default network bits** for now to represent the subnet.
>  I might go back later and edit the article to use the same language as [Professor Messer](https://www.professormesser.com/network-plus/n10-008/n10-008-video/calculating-ipv4-subnets-and-hosts-n10-008/); I should do it now, but I've written over 3,000 words today and I'm tired.

You can also use [subnetting.org](https://subnetting.org/) for practice, but in the meantime, *let's go through some examples.*

![[Subnetting Walk-through-4.png]]
*just a little reminder*
##### Example 1
Let's assume your computer's IP is *192.168.1.10*; how would we figure out how many *subnets are available* to you?

The *default network mask* for the *Class C Private Network 192.168.0.0* is */16* (or *255.255.0.0*)
Your *home network* has a *network address* of *192.168.1.0* and a subnet mask of */24* (or *255.255.255.0*)

This means that there are *8 non-default network bits* in your home network.
2^8=255

There are *255 available subnets* for the default network *192.168.0.0* given a */24* subnet mask.

You could have networks with addresses of 192.168.**1**.0, 192.168.**2**.0, 192.168.**255**.0, etc.


Let's do another.
##### Example 2
Let's assume that your computer's IP is *172.30.1.25*

The *default network mask* for the *Class B Private Network 172.16.0.0* is */12* (or *255.240.0.0*)
Your *home network* has a *network address* of  *172.30.1.0* and a subnet mask of */24* (or *255.255.255.0*)

This means that there are *12 non-default network bits* in your home network.
2^12=4,096

There are *4,096 available subnets* for the default network *172.16.0.0* given a */24* subnet mask.

You would have... lots of networks. Just a whole bunch. I mean, literally over 4,000.


One more time
##### Example 3
Let's say you administer a network for a regional office of a large company. You've been asked to divide the 10.130.0.0/16 network for teams in *Engineering*, *Sales*, *Marketing*, *Business Operations*, and *System Administration*. For the purposes of this exercise, all networks should be the same size with the most *valid host addresses available*.

The *default network mask* for the *given network 10.130.0.0* is */16* (or *255.240.0.0*)
You want to divide the network into *at least* 5 equal networks.

>Remember that thing about **2^x**? You can only equally divide a network into **exponents of 2** (1, 2, 4, 8, 16, 32, etc.)

You can't divide a network equally into 5 pieces. If we were dealing with a large number, we could run the calculations; however, since you know you need more than *4* networks and fewer than *8*, you will need to divide the network into *8 subnets*.
8=2^**3**
This means you will need *3 non-default network bits* to divide the network evenly into 8 subnets.
16 *network* bits + 3 *subnet* bits = */19* subnet mask

If we use the */19* (*255.255.224.0*) subnet mask, we can divide *10.130.0.0* into **at least** 5 equal subnets (for *8 total equal subnets*).

We can check our work by heading over the [SolarWinds](https://www.wired.com/story/the-untold-story-of-solarwinds-the-boldest-supply-chain-hack-ever/) [network calculator](https://www.solarwinds.com/free-tools/advanced-subnet-calculator) and entering our values:

![[Subnetting Walk-through-6.png]]

Looking at this output, you might have noticed that each network will have **8190** available host addresses. While this network is unlikely to run out of host addresses, what if the number of hosts was important? What if we needed to figure out how many hosts there are in a network?

My dear, *astute*, **intelligent**, ***physically attractive*** reader, let's keep going and see how to *calculate the number of hosts in a subnet*.

#### Calculating Hosts

*Calculating hosts* is almost *identical* to calculating networks, just in the opposite direction, forgetting about Public/Private IP networks, and taking into account the *network address* and *broadcast address*.
>Ok, maybe not identical, but pretty close!


(2^(*host bits*))-2 = *number of valid host addresses*

A /16 network has *16 host bits*; if we calculate (2^16) - 2 (for the Network/Broadcast addresses), we get *65,643* **valid host addresses**.

A /26 network has *6 host bits*; so, (2^6)-2 = 62. 

Now you've looked ahead and saw that a */32* network has *0 host bits*; what does it MEAN?!? IT means it's the only "host" on that network! In reality, it's typically only used for [[Loopback interface|loopback interfaces]], and you'll probably see it on routing tables.

>**Note on /31 networks**
	If you've done the calculations, you know that a /32 network is a single host, and a /30 network only supports two *valid IP addresses*, but what about /31 networks? There are two IP addresses available, but they should both be taken by the network address and the broadcast address, right? Well, /31 networks have been defined in [RFC 3021 - Using 31-Bit Prefixes on IPv4 Point-to-Point Links](https://datatracker.ietf.org/doc/html/rfc3021). Not all networking gear handles /31 networks correctly, and you will probably not be asked about /31 networks on the CCNA.

You can also use [subnetting.org](https://subnetting.org/) for practice, but in the meantime, *let's do an exercise*.

##### Example 1
Let's say you administer a network for a small non-profit. You've been asked to divide the **192.168.10.0/24** network for teams in *Research*, which needs 22 valid host addresses, *Community Outreach*, which needs 53, *Business Operations*, which needs 13, and *Lizard People*, which needs 3.

Like when dividing a network, *each subnet* must be *split* into one of *2's exponents*.
![[Subnetting Walk-through-4.png]]

| Bit Position               | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
| -------------------------- | --- | --- | --- | --- | --- | --- | --- | --- |
| Total Addresses            | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| Available Hosts ((2^x)-2)  | 126 | 62  | 30  | 14  | 6   | 2   | 2   | 1   |
| Slash-notation subnet mask | /25 | /26 | /27 | /28 | /29 | /30 | /31 | /32    |

The first step is to organize your networks by order most hosts to fewest, and go from there.
*Community Outreach*: 53
*Research*: 22
*Business Operations*: 13
*Lizard People*: 3

Next, you can run through the (2^x)-2 calculations to find which subnets can carry the correct number of hosts. I find it's helpful to clearly label the information we're looking for in each subnet.

*Community Outreach*
- Minimum hosts: *53*
- Subnet Slash Notation: */26*
- How many total addresses? *64*
- How many valid hosts? *62*
- What's the network address? *192.168.10.0*
- What's the broadcast address? *192.168.10.63*
	- Remember, this is the last address in subnet with 64 total address, but starts at 0
*Research*
- Minimum hosts: *22*
- Subnet Slash Notation: */27*
- How many total addresses? *32*
- How many valid hosts? *30*
- What's the network address? *192.168.10.64*
- What's the broadcast address? *192.168.10.95*
	- Remember that counting starts at .64, so the broadcast address is one less than you think
*Business Operations*
- Minimum hosts: *13*
- Subnet Slash Notation: */28*
- How many total addresses? *16*
- How many valid hosts? *14*
- What's the network address? *192.168.10.96*
- What's the broadcast address? *192.168.10.111*
*Lizard People*
- Minimum hosts: *3*
- Subnet Slash Notation: */29*
- How many total addresses? *8*
- How many valid hosts? *6*
	- This is ideal for when the *Lizard People* divide through [mitosis](https://en.wikipedia.org/wiki/Cell_division)
- What's the network address? *192.168.10.112*
- What's the broadcast address? *192.168.10.119*

And you're all set! Each of the following groups will get these networks: 
*Community Outreach*: 192.168.10.0/26 (*255.255.255.192*)
*Research*: 192.168.10.64/27 (*255.255.255.224*)
*Business Operations*: 192.168.10.96/28 (*255.255.255.240*)
*Lizard People*: 192.168.10.112/29 (*255.255.255.248*)

#### Subnetting Recap

**Memorize the Private IP ranges.**
![[IPv4 Address Classes#Private IPv4 Address Ranges]]

**Calculate the number of subnets available in a given network**
2^(subnet bits) = Number of available, equally-sized networks

**Calculate the number of valid host addresses in a given network**
(2^(host bits))-2 = Number of valid host address
- You subtract 2 from the total to account for the *network address* and *broadcast address*

>Ok, that about covers the basics; let's get on to how this applies for the **CCNA**

## Preparing to Subnet Under Pressure

On the CCNA, you will have between 90 and 120 questions, and 120 minutes to answer them ([New CCNA exam - 200-301](https://study-ccna.com/new-ccna-exam-200-301/)). I can feel your existential dread; *how am I supposed to calculate all that crap when I have just over a minute to answer each question?*

If you've read through the above guide or studied with Jeremy's IT lab, then **congratulations!** You've laid the groundwork. Now it's time to build a... house... network? The analogy ran away from me.

*Anyway*, there's a shortcut, called...
### [The Magic Number](https://www.professormesser.com/network-plus/n10-008/n10-008-video/magic-number-subnetting-n10-008/)
Messer goes into great detail, but the basic idea is that *octets increment* by the *bit-value* of the *last bit* in the *subnet mask*.

This means that we can quickly comprehend the *size of a network* just by knowing the *subnet mask* alone. 🤯

Let's review the bit values in an *octet*:
![[Subnetting Walk-through-4.png]]

The bit value **directly correlates** with the size of the network in that octet.

For example, the subnet mask */19* (*255.255.224.0*) falls on the *5th bit*, which has a value of *32*. This means that whatever *network* is being subnetted *will have a range of* (or will *increment by*) *32*.

>It might be easier for you to think of bit position as **1 to 8** from left to right, and that's perfectly alright.
>The above example would then fall on the **3rd bit** with a value of **32**.
>For consistency, I will use the bit-positions I reference above, but hopefully this doesn't just make it more confusing - let me know.

If you needed to subnet the network *192.168.0.0/16* into */19* subnets, it's dead simple; it *increments* by *32*
192.168.*0*.0 - 192.168.*31*.255
192.168.*32*.0 - 192.168.*63*.255
192.168.*64*.0 - 192.168.*95*.255
... and so on. 

Let's take this a step further.

Start by setting mental anchors; complete octets come naturally (*/8*, */16*, and */24*).
I found it helpful to pick midpoints as well because I tend to get a little lost in the middle. I went with */4*, */12*, */20*, and */28*, because they fall on *4th* bit in each *octet* leaving an even *dotted-decimal* value of *240*, and a *bit-value* of *16*.

I write these *slash-subnets* out, followed by their *dotted-decimal* equivalent, followed by the *bit value*. Writing it as a list can help you to *visualize the information*, making it easier to recall and identify patterns.

4,240,16
8,255,1
12,240,16
16,255,1
20,240,16
24,255,1
28,240,16

As a neurodivergent person, I also found it helpful at the start of the exam to *write the whole list on the whiteboard*. This gave me something to lean on near the end of the exam when *every second counts*.

4,240,18
5,248,8
6,252,4
7,254,2
8,255,1
9,128,128
10,192,64
etc.

>If you're unsure which type of list you'll need, practice subnetting at [subnetting.org](https://subnetting.org/), and each time, write out the list of your choice as reference.
>	This will help you memorize it, and give you information on how often you refer to it, where you get caught up, etc., and you can adjust it as needed.

As we discussed earlier, the *bit value* is the **magic number** to quickly comprehending the scope of a network. The *first* octet in a */6* network increments by *4*; the *second* in a */10* network increments by *64*, and so on.

However, it's almost always faster to just *know* the answer instead of having to look it up. Therefore, I've included a link below to *Anki flashcards* I created that specifically to reinforce your translation from *dotted-decimal* to *slash-notation* and back again.
There are also cards that give you a *slash-notation subnet mask* and ask you to say *which octet increments* and by *how much*. I hope they're as helpful to you as they were to me.

As you memorize this information, go to [subnetting.org](https://subnetting.org/) and do rapid-fire practice. You might have used it to practice the proper calculation methods, but *it's more realistic* to try to *complete as many as you can* within a *short time limit*. Think of it less as a chore, and more like a game (I find it exercises similar brain-muscles as *sudoku*^[Incidentally, "sudoku" is an abbreviation of a Japanese phrase which means "huge waste of time"]). At least, that's what I told myself.

#### Study Prep Recap
The *bit value of the last bit in a subnet mask* indicates the *IP range* of the *subnet's* **octet**
- For example, 10.20.32.0 */20* has a *final subnet bit bit-value* of *16*, and so the *third octet* will increment by 16
	- 10.20.**32**.0 - 10.20.**47**.255, 10.20.**48**.0 - 10.20.**63**.255, etc.

Create a *list* of *subnets*, *magic numbers*, and anything else you find helpful, and *fine-tune it* for use on the *exam*.

1. Prep
	1. Set mental anchors and write lists of subnet masks and bit values
2. Study
	1. Anki Flashcards
		1. These flashcards should help you practice quickly recalling *subnet* and *magic number* information
		2. [010 Subnetting.apkg](https://www.dropbox.com/scl/fi/7cv5kurglrzagfmz5tpby/010-Subnetting.apkg?rlkey=3n977c7sq98ojnnumwdistdw8&dl=0)
	3. [subnetting.org](https://subnetting.org/)
		1. When you're sitting on the toilet, waiting for your game to load, or winding down for bed, go to [subnetting.org](https://subnetting.org/) and answer as many questions as you can
			1. Think of it like playing sudoku, just simple mind problems.
		2. **Be kind to yourself if you get them wrong.** You will make mistakes, and that just means *you're learning*.
3. Exam time
	1. *Write out your list* of *subnet masks* and *bit-values* on the *whiteboard* 
	2. *Feel confident* that you've done so much to prepare; you are *awesome*.
