
## 2026.09.10 Meeting
- Look a little bit more into diabetes
	- Need to make sure it is a problem worth solving
	- I.e., it isn't extremely easy to detect the changes --> meaning, early warning is important 
- Worth looking into --> other diseases that are less obvious to provide an early warning
	- But, would also need some possible features to provide an early warning
	- Could still be diabetes, but need to look into it more
- Explainable AI --> may look into an expert system (based on rules) combined with deep learning later on
	- Possibly multiple expert systems --> weigh their opinions using Dempster-Shafer theory --> better and explainable answer
		- Dempster-Shafer theory --> reasoning with uncertainty
- Existing research for at-home detection or hospital detection (assistant to the doctor)
	- And which features we need for each direction 
- Problem --> check paper "conclusion", is it useful or not?
	- E.g., just detecting the flow of COVID-19 severity isn't that interesting
		- We know cases are less severe now
		- But, detecting concept drift and forecasting future years is more interesting
- Meeting same time next week (2pm on Thursday)

## 2026.09.03 Meeting
- Big changes in dataset need to be detected --> such as transition from stage-to-stage of diabetes
	- Could call it "early warning of stage drift"
	- Small changes can be adapted to with real-time training, but for major detection --> need full/partial re-training
- First paper --> check for large changes within the model (concept drift/stage changes)
	- Similar idea to auto-encoder storm paper where you need to verify the change to prevent false positives on pure noise
- Two models
	- Model 1 --> actually predict the diabetes condition
	- Model 2 --> detecting actual drift in the data to determine if the disease will move to a new stage
- Understand the details of the diabetes disease before creating model
- Look into different sufficient models for both tasks --> autoencoder GRU (like the anomaly storm paper) or maybe a more modern transformer architecture
- First published conference paper --> something similar to the anomaly storm detection paper (early warning)
- Possibly target the [ICMI IEEE conference](https://www.icmiconf.com/) again
	- Paper deadline --> December 15th, 2026
	- Conference dates --> May 01 + 02, 2027
- Then, work on extending into a journal paper during next Spring + Fall 2027 semesters
- Meeting minutes --> send over right after meeting


## 2026.08.21 Meeting
- Understand the details of the diabetes disease before creating model
- Different models should be used for different stages
	- Monitoring the signals of diabetes
	- Early detection before the patient goes to the doctor
- Two phases for now:
	- Detecting concept drift in diabetes 
	- Apply different models with real-time training for early detection of diabetes (including worsening)
- For now: focus on concept drift and early detection
- Real-time training is only really necessary when concept drift is actually detected --> used to adapt the model to the
- Thursday afternoon at 2pm



## 2026.08.13 Meeting
- Main topic: choosing dissertation topic and discussion of research papers
- Focus on real concept drift --> function modeling the relation between X and Y, P(Y | X), actually changes
	- Opposed to fake/phony concept drift, where the relationship between X and Y changes, but it is due to a missed feature *e*
- Look into latest journal paper on personal website --> topic is anomaly detection using an auto-encoder







# References
