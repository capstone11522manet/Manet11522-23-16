Group: 9785-23-7
Date & Time: Friday 4/8/23, 11:20am - 11:45am
Present: Curtis, Daniel, Ellie, Yibe
Apologies: Nil
Method: Virtual; Microsoft Teams
Next Meeting: Saturday 5/8/23, afternoon


#### Goals of the project:
* Different aspects of project:
	* Dan more interested/focus on ML aspect, and creating algorithm from training data (generated data from base simulation)
	* Curtis focus on simulation aspect; simulating cooperative black hole network, outputting pcap file to be fed into Dan's ML, later running trained algorithm against network to discover and avoid identified malicious nodes
	* Ellie focus on going through relavant literature, identifying what's been done and attempted by other people - in what way are we going to contribute something novel - especially novel approach to machine learning, which may have been implemented elsewhere
* Looking to make a network where multiple black hole nodes contribute to fool other nodes, and still (relatively) accurately identify those contributing nodes
* Create simulation by altering cpp (including .cc and .h) files within ns3
* Goal Flow should be:
	* (Novel approach)
	* Simulate network with block hole nodes
	* Feed pcap/captured data to teach ML algorithm
	* Apply algorithm to currently running network topology
		* Initial runs will likely be running with training algorithm from fresh, but goal is to have this applicable to real-world networks that wouldn't be in a position to stop and start all the time. Applying a new algorithm while running is the desired state.
* Want final product to be efficient enough for battery-powered nodes (e.g. IoT network, bespoke mobile networking devices, etc.)

#### Approval note for first assignment (due tonight)
* Yibe recommended keeping the solution of "screenshot of email attached to EOI", but also recommended responding to convener-its email distribution and Cc'ing him.

#### GitHub account info from group members and yibe to provide access to github project
* All group members added to GitHub project
* Main repository (forked from previous UC CAPSTONE project "Manet11522-23-16") publicly available
* Curtis to send Yibe an email to find his GitHub credentials, so he can be across the Project's progress

#### University resourcing
* Part of UC CAPSTONE project is funding of $350 towards procurement to undertake the project - we'll currently assume rental of Jupyter Notebook (laptop?) hardware/associated Azure cloud instances to fall under this allotment
* Group tasked with researching and defining a methodology to create a virtualised image of the laptop/notebook resource, which Yibe has offered to then host on Azure - enabling full remote access to resourcing for group members
	* Snapshotting of the Azure vm/resource should be considered, especially before understanding of NS3 has developed to the point where troubleshooting is easier
* Yibe will show group members laptop/notebook resource Monday 7/8/23 in the afternoon

> Meeting minutes currently recorded in markdown format. If required for submission for CAPSTONE project, they will be transposed to another word processor application format (likely .docx or .odf) and split between "agenda, discussion, action items, and other business" sections. Future meetings will possibly follow that structure closer than today's meeting/minutes, in order to make future transposition easier (if necessary).