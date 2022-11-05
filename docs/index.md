# Learning Health System Practical Guide
AJ Chen, PhD, Co-Chair of [LHS Tech Forum Initiative](https://www.learninghealth.org/2020-lhs-technology-forum), Learning Health Community

[Work in progress]

# Summary

This Learning Health System (LHS) Quick Guide is focused on providing practical information for developers and health organizations to get started with developing LHS quickly.
The contents of the quick guide is based on my understanding and interpretation of the series of LHS reports from the National Academy of Medicine (NAM, formerly Institute of Medicine, IOM) and the progress made so far in the emerging field of LHS. 

The guide first summarizes the NAM LHS reports in order to answer the fundamental questions: Why do we need LHS? What is LHS? Who are building LHS? 

Then, it briefly describes the recent technology developments that are needed to build small units of LHS with machine learning (ML). The highlight is on the first simulation of ML-enabled LHS (ML-LHS) using synthetic patient data, which is openly available at [Open Synthetic Patient Data](https://github.com/lhs-open/synthetic-data) on GitHub. For demonstration purpose, it shares example projects from hospitals that are building real patient ML-LHS units for different tasks such as disease risk prediction. A new "synthetic+real" strategy is proposed for building ML-LHS units more efficiently. 

The subsequent sections provides more detailed information on electronic medical record (EMR) or electronic health record (EHR) data, synthetic patients, data-driven machine learning, and other technology components essential for ML-LHS. 

After reading this quick practical guide, hopefully you will become more familiar with LHS and ready to research on ML-LHS in your environment.  

The guide's main goals:

>1.	Provide technical information for developers and health organizations to quickly understand the benefits of LHS and get started with LHS.
>2. Explain it is more practical to build small ML-LHS units rather than being bogged down in the grand LHS picture.
>3. Propose a new "synthetic+real" strategy: simulate ML-LHS unit with synthetic patients first and then apply the process to build ML-LHS unit with real EHR data.

Based on the limited progress of LHS, I also make two hypotheses in the guide, which may encourage more research on ML-LHS:

>   - Hypothesis 1: Due to its inherent data-centric ML approach, ML-LHS can ultimately achieve high prediction performance (>95%) for most diseases and conditions. 
>   - Hypothesis 2: ML-LHS over hospital-led clinical research networks can effectively enable small clinics with seamlessly disseminated ML models and thus help reduce health care disparities in underserved populations.

The LHS quick guide is part of the [Open LHS Project](https://github.com/lhs-open) on GitHub, aimed to help advance the emerging field of learning health systems. As a dynamic technical documentation for LHS, this guide is published on [GitHub Pages](https://lhs-open.github.io/lhs-guide/). It will be updated when new LHS information becomes available. It is open source at https://github.com/lhs-open/lhs-guide on GitHub. 

<br>

# 1. The vision of Learning Health Systems

## The LHS vision from NAM

>   “In a learning health system, science, informatics, incentives, and culture are aligned for continuous improvement and innovation, with best practices seamlessly embedded in the delivery process and new knowledge captured as an integral by-product of the delivery experience.”  (Source: NAM website - [The Learning Health System Series](https://nam.edu/programs/value-science-driven-health-care/learning-health-system-series/))

The LHS vision was created by NAM/IOM and described in a series of reports from NAM. Below I will summarize the related information in the reports to show why LHS is needed and what LHS is. Some examples are also chosen from the reports. For details, please see [The Learning Health System Series](https://nam.edu/programs/value-science-driven-health-care/learning-health-system-series/) on NAM website.

## Why do we need LHS? 

![NAM report](img/The-Learning-Healthcare-System-195x300.jpg) 

In 2006 the IOM Roundtable on Evidence-Based Medicine convened a workshop entitled “The Learning Healthcare System”, from which the first NAM LHS report "The Learning Healthcare System" was published in 2007. The report recognizes that the performance of the healthcare system remains far short of where it should be. After dissects the process of clinical evidence generation and application, the report envisions a new health care system in which both evidence development and application flow seamlessly and continuously in the course of care, i.e. a learning health system.  

A re-evaluation of how health care is structured to develop and apply evidence subsequently identified the following problems in current health care systems:

>- Problem: Missed opportunities, preventable illnesses, and injuries are too often in health care.

Medical errors: IOM 2001 report “Crossing the Quality Chasm” found an estimated 44,000 to 98,000 Americans may die annually due to medical errors. This alarming problem underscores the need for redesigning health care to address the key dimensions on which improvement was most needed: safety, effectiveness, patient centeredness, timeliness, efficiency, and equity. (IOM 2001)

>- Problem: The prevailing approach to generating clinical evidence is inadequate today and may be irrelevant tomorrow, given the pace and complexity of change. 

The current dependence on the randomized controlled clinical trial (RCT), as useful as it is under the right circumstances, takes too much time, is too expensive, and is fraught with questions of generalizability.

Evidence lacking generalizability: Clinical research studies often do not reliably generate evidence that is generalizable for clinical decision making in real-world patient populations. The use of strict inclusion and exclusion criteria restricts a broader clinical population from participating in clinical studies. As such, even when lengthy clinical trials are completed, clinicians may not feel that study results can be applied to their own, often more complex, patient populations. For example, Masoudi and colleagues demonstrated that only a minority (13% to 25%) of persons with heart failure in clinical practice would qualify for enrollment in clinical trials (Masoudi 2003).

>- Problem: Deficiencies are in the quantity, quality, and application of evidence.

Improvement requires a stronger system-wide focus on the evidence. A new clinical research paradigm that takes better advantage of data generated in the course of healthcare delivery would speed and improve the development of evidence for real-world decision making.

>- Problem: The current approaches to interpreting the evidence and producing guidelines and recommendations often yield inconsistencies and confusion. Dissemination of guidelines is too slow.

One report suggested that it may take as long as 17 years to turn some positive research results to the benefit of patient care (Balas and Boren 2000). Need to reduce the lag time between innovation and its implementation.

>- Problem: Inefficiency and waste are in much of health care.

At system level, it is clear that the clinical research enterprise is detached from the clinical care delivery process. The report proposes that embedding clinical research in clinical delivery may fix this foundational defect in the health care systems. Because carrying out research and care simultaneously makes continuous learning and dissemination more efficient and effective, it may drastically improve care quality and reduce cost at the same time. This is why we need learning health systems.

## What is LHS?

SOURCE: NAM 2007 LHS report – The Learning Healthcare System.

Through reengineering clinical research and healthcare delivery, the report hopes that the process of generating and applying the best evidence will be natural and seamless components of the process of care itself, as part of a learning healthcare system, which can be both more effective and more efficient than we have today. 

Learning Health System Characteristics:
>-  Culture: participatory, team-based, transparent, improving
>-  Design and processes: patient-anchored and tested
>-  Patients and public: fully and actively engaged
>-	Decisions: informed, facilitated, shared, and coordinated
>-	Care: starting with the best practice, every time
>-	Outcomes and costs: transparent and constantly assessed
>-	Knowledge: ongoing, seamless product of services and research
>-	Digital technology: the engine for continuous improvement
>-	Health information: a reliable, secure, and reusable resource
>-	The Data utility: data stewarded and used for the common good
>-	Trust fabric: strong, protected, and actively nurtured
>-	Leadership: multi-focal, networked, and dynamic

The Office of National Coordinator (ONC) envisioned a nationwide learning health system (Friedman 2010). 

## Redefining LHS

SOURCE: NAM 2013 report - Best Care at Lower Cost.

In 2013, IOM produced another report to re-iterate its vision of LHS: “Best Care at Lower Cost: The Path to Continuously Learning Health Care in America.” It explores the imperatives for change, the emerging tools that make transformation possible, the vision for a continuously learning health care system, and the path for achieving this vision. 

![NAM report](img/Best-Care-at-Lower-Cost-200x300.jpg) 

Redefining the needs for transforming the current “broken” healthcare systems to learning health systems:

>-	Need a new approach to medical knowledge generation and application.

The current approach to generating new medical knowledge falls short in delivering the evidence needed to support the delivery of quality care. The evidence base is inadequate, and methods for generating medical knowledge have notable limitations.

The gap between the evidence possible and the evidence produced continues to grow, and studies indicate that the number of guideline statements backed by evidence is not at the level that should be expected. In some cases, 40 to 50 percent of the recommendations made in guidelines are based on expert opinion, case studies, or standards of care rather than on multiple clinical trials or meta-analyses.

The current research knowledge base provides limited support for answering important types of clinical questions, including those related to comparative effectiveness and long-term patient outcomes. 

The inadequacy of the evidence base for clinical guidelines has consequences for the evidence base for care delivered. Estimates vary on the proportion of clinical decisions in the United States that are adequately informed by formal evidence gained from clinical research, with some studies suggesting a figure of just 10-20 percent.

>-	Need rapid dissemination.

The example of the diffusion of the use of beta-blockers after heart attack is a success story in many ways: high-quality evidence was produced; it was incorporated into clinical care guidelines, quality improvement initiatives, and quality-of-care measures; and several health plans offered financial incentives for its uptake. Yet even with this level of effort, it took 25 years from the time the initial results were published until the time the treatment saw general use in clinical practice. This example speaks to the need to create infrastructure that makes the process of learning and improvement easier, so that the next discovery does not require 25 years of sustained effort before it is widely used to help patients.

>-	Need to control the unsustainable healthcare cost.

Improving quality and controlling costs requires moving from this unsustainable and flawed organizational arrangement to a system that gains knowledge from every care delivery experience and is engineered to promote continuous improvement. In short, the nation needs a health care system that learns, and a learning health care system is both possible and necessary for the nation today. 

**Definition for Learning Health Care System:**
> “A learning health care system is one in which science, informatics, incentives, and culture are aligned for continuous improvement and innovation, with best practices seamlessly embedded in the care process, patients and families active participants in all elements, and new knowledge captured as an integral by-product of the care experience.” (Source: NAM 2013 report - Best Care at Lower Cost.)
 
<br>

**Schematic of a learning health system:** 
![LHSpic](img/nam-lhs.png) 

Source: NAM 2013 report - Best Care at Lower Cost.

<br>

## Characteristics of a Continuously Learning Health Care System
SOURCE: NAM 2013 "Best Care at Lower Cost" report.

Science and Informatics:

-	Real-time access to knowledge — A learning health care system continuously and reliably captures, curates, and delivers the best available evidence to guide, support, tailor, and improve clinical decision making and care safety and quality.

-	Digital capture of the care experience — A learning health care system captures the care experience on digital platforms for real-time generation and application of knowledge for care improvement.

Patient-Clinician Partnerships:

-	Engaged, empowered patients — A learning health care system is anchored on patient needs and perspectives and promotes the inclusion of patients, families, and other caregivers as vital members of the continuously learning care team.

Incentives:

-	Incentives aligned for value — A learning health care system has incentives actively aligned to encourage continuous improvement, identify and reduce waste, and reward high-value care.

-	Full transparency — A learning health care system systematically monitors the safety, quality, processes, prices, costs, and outcomes of care, and makes information available for care improvement and informed choices and decision making by clinicians, patients, and their families.

Continuous Learning Culture:

-	Leadership-instilled culture of learning — A learning health care system is stewarded by leadership committed to a culture of teamwork, collaboration, and adaptability in support of continuous learning as a core aim.

-	Supportive system competencies — A learning health care system constantly refines complex care operations and processes through ongoing team training and skill building, systems analysis and information development, and creation of the feedback loops for continuous learning and system improvement.


## Who are building LHS?

LHS Examples:

-	Intermountain Healthcare: Feedback Loops to Expedite Study Timeliness and Relevance.
-	Geisinger Health System: Use of Electronic Health Records to Bridge the Inference Gap.
-	Department of Veterans Affairs: Implementing evidence-based practice, particularly via use of the electronic health record.

Examples of clinical research networks as LHS:

-	Kaiser Permanente
-	NCI cancer research network
-	HMO research network (HMORN)
-	Patient-Centered Network of Learning Health Systems (LHSNet)

## LHS definition for developers

For easier understanding by developers, this guide provides a simpler technical definition for LHS:
>-	A learning health system has research embedded in the health care services where health data are collected simultaneously, new knowledge and models are learned continuously, and improvement can be deployed seamlessly. 

The "learning" in Learning Health System means machine learning, continuous learning, and ultimately self-learning in addition to normal learning by human. When research and practice are seamlessly integrated, the dissemination problem starts to ease.

In essence, LHS is about revolutionizing knowledge generation and use in medicine. The next two sections dive deeper into the "knowledge business".

<br>

# 2. Evidence and Knowledge Generation

## Study methods
[SOURCE: NAM 2013 "Best Care at Lower Cost" report]

Randomized clinical trials (RCT) are the “gold standard” of the current clinical research enterprise for generating medical evidence and knowledge. Despite the accelerating pace of scientific discovery, the current clinical research enterprise does not sufficiently address pressing clinical questions. The result is decisions by both patients and clinicians that are inadequately informed by evidence.

The evidence basis for clinical guidelines and recommendations needs to be strengthened. In some cases, 40 to 50 percent of the recommendations made in guidelines are based on expert opinion, case studies, or standards of care rather than on multiple clinical trials or meta-analyses.

Even at the current pace of production, the knowledge base provides limited support for answering many of the most important types of clinical questions. A study of clinical practice guidelines for nine of the most common chronic conditions found that fewer than half included guidance for the treatment of patients with multiple comorbid conditions.

The cost of current methods for clinical research averages $15-$20 million for larger studies — and much more for some — yet the studies do not reflect the practice conditions of many health care providers.

New methods are needed to address current limitations in clinical research. The alternative research methods include:

-	adaptive trials
-	delayed design trials
-	cluster randomized controlled trials
-	observational trials
-	case-control studies
-	pragmatic clinical trials (PCT)
-	large simple trials (LST)

Alternative methods require different statistical analysis: e.g.

-	New Bayesian techniques for data analysis can separate out the effects of different clinical interventions on overall population health.
-	Modeling physiological pathways and disease states.
-	Machine learning.

## Experimental vs. observational study

**Experimental method:**

-	Can employ randomization, can confer protection from certain bias, time-consuming and costly.
-	While the randomized controlled trial has a highly successful track record in generating new clinical knowledge, it has several limitations: not practical or feasible in all situations; expensive and time-consuming; address only the questions they were designed to answer; cannot answer every type of research question.

**Observational method:** 

-	Can only randomize at group level, easier to collect data in the process of care delivery, results closer to real-world setting, requiring less time and less cost. 
-	The strength of observational studies is that they capture health practices in real-world situations, which aids in generalizing their results to more medical practices. This research design can provide data throughout a product’s life cycle and allow for natural experiments provided by variations in care. However, observational studies are challenged to minimize bias and ensure that their results were due to the intervention under consideration.

## Observational study method in LHS

NAM 2013 report, “Observational Studies in a Learning Health System: Workshop Summary” (OS-LHS), reviews leading approaches to observational studies, how to deal with bias, how to evaluate treatment heterogeneity, and other important aspects of using observational study method in LHS.

Observational studies can provide information on the effectiveness of therapies in real-world clinical practice. The observational study method complements the RCT method, with the following features:

-	Detect signals about the benefits and risks of various therapies in the general population.
-	Identify rare side effects and benefits that are beyond the reach of RCTs.
-	Provide community-level data that can lead to new hypotheses that can then be tested in clinical trials. 
-	Provide data for developing predictive models.
-	Provide estimates of effectiveness tailored to individual patients。
-	Used in conjunction with RCTs to test the external validity of the RCTs in a more representative population and assess the heterogeneity of the treatment response. 

Issues of the observational study method: 

-	Potential bias. 
-	Data quality issues
-	Analytical challenges
-	Harder to draw causal relationships.

About bias:

-	Missing information and misclassified information that are directly or indirectly related to the health outcomes of interest may cause bias. 
-	The instrumental variable method is one approach to controlling for unmeasured confounding.

Because of the potential bias, an observational study needs careful design in order to prevent misleading results. Lessons can be learned from these examples:

-	The conflicting findings for hormone replacement therapy between a large number of observational studies and the RCT conducted by the Women’s Health Initiative.

According to Dr. Steven N. Goodman at the Stanford University School of Medicine, “observational studies and RCTs are getting closer and closer. The choice between them is really not, in a sense, a choice between them but involves a lot of complicated trade-offs and questions about what each one reveals that the other one does not.”

Dr. Goodman explained the foundational equation of epidemiology: 

`Pr(outcome | X = x) = Pr[outcome | set(X = x)]`

-	The probability (Pr) of an outcome with an observed risk factor (X) is equal to the probability of that outcome when that risk factor is set equal to the same value (x). 
-	The equation can also be posed as a question: Is the observed effect the same as the effect seen when the variable is actively manipulated? If the answer to that question is “yes,” then the result of the observational study can be transferred into the realm of practice.

## Large simple trial study method in LHS

NAM 2013 report, “Large Simple Trials and Knowledge Generation in a Learning Health System: Workshop Summary” (LST-LHS), describes the LST research method in the context of LHS and provides successful examples. 

Large simple trial can answer certain questions about the effectiveness of drugs and other interventions at less cost or in less time, or both, than the randomized clinical trial.

The report describes the infrastructure required for conducting LST. Utilization of EHR is essential to collect and manage data for a large number of patients. EHRs enable performing clinical trials at the point of care. 

Clinical research networks (CRN) or organizational consortia may be required to recruit enough number of patients from many health care organizations. These networks are evolving toward the learning health care system model. Within CRNs, clinicians and researchers can learn from a much larger base of patients, and examine the outcomes of widely varying diagnostic and treatment practices and identify factors that lead to better outcomes. CRNs can conduct clinical trials with much larger populations, which is especially important for rare or less common diseases.
  
Data standards, such as the Clinical Data Acquisition Standards Harmonization (CDASH) from FDA’s initiative, exists and electronic tools are available to collect data from heterogeneous EHRs. 

For details, see presentations from the following experts in the report:

-	Dr. Richard Platt from Harvard Medical School. 
-	Dr. Ryan E. Ferguson from VA.
-	Rebecca Daniels Kush from the Clinical Data Interchange Standards Consortium
-	Carole M. Lannon from Cincinnati Children’s Hospital Medical Center

## Challenges and new opportunities

In 2016, NAM organized a meeting: Accelerating Clinical Knowledge Generation and Use, and published a discussion paper "Generating Knowledge from Best Care: Advancing the Continuously Learning Health System" (Abraham 2016). According to the report, despite the promise of embedded learning activities, barriers to operational and research collaboration remain.

After the NAM LHS report series were released, EMR has quickly become ubiquitous in health care organizations. At the same time, machine learning and artificial intelligence (AI), which were under-explored in the NAM LHS reports, have unexpectedly become common research tools for any clinical researchers to use, thanks to the rapid advance of computing power and algorithm development in recent years. 

In my view, this environment of unprecedent digital health data plus machine learning is giving rise to unforeseen possibilities for medical knowledge generation and beyond in the context of LHS. On one hand, a large number of machine learning studies have directly used routine EMR data to learn and build knowledgebases about clinical events such as diagnoses and treatments. On the other hand, ML models are being built from EMR data without prior knowledge or generating traditional form of knowledge. ML models, particularly those uninterpretable models, will push the traditional concept of learning and disseminating new knowledge in LHS into an uncharted territory - disseminating machine learning models without knowledge about or from the models (a situation where we just know it works but don’t know how). 

<br>

# 3. Knowledge and Model Dissemination

## Dissemination through knowledge-based CDS 
[SOURCE: NAM 2013 "Best Care at Lower Cost" report]

Current systems that generate and implement new clinical knowledge are largely disconnected and poorly coordinated. While clinical data contribute to the development of many effective, evidence-based practices, therapeutics, and interventions every year, only some of these become widely used. Many others are used only in limited ways, failing to realize their transformative potential to improve care.

Evidence suggests that simply providing information, albeit more quickly, rarely changes clinical practice. The challenge, therefore, is how to diffuse knowledge in ways that facilitate uptake by clinicians.

One technological tool for bringing research results into the clinical arena is clinical decision support. A clinical decision support system integrates information on a patient with a computerized database of clinical research findings and clinical guidelines. The system generates patient-specific recommendations that guide clinicians and patients in making clinical decisions.

As the pace of knowledge generation accelerates, new approaches are needed to deliver the right information, in a clear and understandable format, to patients and clinicians as they partner to make clinical decisions. Related findings:

-	The slow pace of dissemination and implementation of new knowledge in health care is harmful to patients. For example, it took 13 years for most experts to recommend thrombolytic drugs for heart attack treatment after their first positive clinical trial.
-	Available evidence often is unused in clinical decision making. One analysis of the use of implantable cardioverter-defibrillator (ICD) implants found that 22 percent were implanted in circumstances outside of professional society guidelines.
-	Decision support tools, which can be broadly provided in electronic health records, hold promise for improving the application of evidence. One study found that digital decision support tools helped clinicians apply clinical guidelines, improving health outcomes for diabetics by 15 percent.

## Dissemination through models

Data from electronic health records, although imperfect, yield reasonably accurate statistical prediction models that are often better than those based on the simple staging strategies currently used to predict risk. (NAM 2013 OS-LHS report)

As I described in the previous knowledge generation section, machine learning models can be built from a whole EMR or a number of EMRs. Depending on the algorithms used, some are interpretable but some are not. There will be challenges in disseminating the uninterpretable ML models even though they are high-performance. 

<br>

# 4. Building LHS

## The NAM report’s approach

NAM 2011 report “Digital Infrastructure for the Learning Health System: The Foundation for Continuous Improvement in Health and Health Care” explores current efforts and opportunities for leveraging current technologies and identifying priorities for innovation in order to ensure that data collected in one system can be utilized across many others for a variety of different uses. However, a complete and coherent picture of LHS infrastructure is still not clear.  

NAM 2011 report, “Engineering a Learning Healthcare System: A Look at the Future: Workshop Summary”, reviews engineering approaches to continuous feedback and improvement on quality, safety, knowledge, and value in health care. The goal of a learning healthcare system is to deliver the best care every time, and to learn and improve with each care experience. Currently, the organization, management, and delivery of health care in the United States falls short of delivering quality health care reliably, consistently, and affordably. The report takes stock of lessons from engineering that might be applicable to health. However, it does not provide guidance for building an actual LHS.

The NAM 2013 "Best Care at Lower Cost" report presents a complex LHS, and it concludes: “Given the complexity of the system and the interconnectedness of its various sectors, no one sector acting alone can bring about the scope and scale of transformative change necessary to develop a system that continuously learns and improves.” (Chapter 10, page 281).

## This guide’s bottom-up approach

The NAM report’s above conclusion may be true if LHS is only defined as a ultimate national learning health system. But, it may not be a productive approach - the LHS is so complicated that no one can start building it. 

I think, for practical purpose of implementation, we should define and make learning health systems at different levels in a series of stages. Most importantly, the starting point should be the kind of LHS that can be built now by one hospital, one department, or one small group without unnecessary external dependency. 

Therefore, this LHS quick guide takes a practical bottom-up approach: break down a large complex LHS into **small LHS units**; design and build the LHS units to perform specific tasks of problem solving; and then connect the functional LHS units to sub-systems. When many sub-systems running smoothly, then integrate the subsystems to larger learning health systems. 

Since we are still in the beginning of building learning health systems, we should be focused on building enough number of small LHS first for demonstrations. What would be low-hanging fruits for LHS at this stage? Predictive LHS base on EMR data! For example, it would be more likely to make a strong business case for risk prediction LHS to increase disease early detection or medication prediction LHS to implement personalized medicine in hospitals. 

## Focus: Building small ML-enabled LHS units

This guide is focused on providing practical guidance and examples for building small ML-enabled LHS units (ML-LHS). Enabled by machine learning, the predictive or other functional ml-LHS units are expected to effectively improve the performance of many specific tasks for clinical care or public health.

ML-LHS unit's key characteristics:

1. Data-driven.
2. Machine learning. 
3. Continuous learning.
4. Rapid dissemination.
5. Automation.

Development of small but effective ML-LHS is made easier by the open data and software that were not available when the NAM reports were written. These include a large number of free and open source machine learning algorithms and tools to choose from now. Although limited, some shared EHR patient data can be obtained from sources with permission. For many diseases, synthetic patients can also be generated by recent technologies like Synthea to supplement the real EHR data. Synthetic data can be used to develop ML algorithms and LHS processes for testing or training purpose.  

In the following sections, the first simulation of risk prediction LHS with synthetic patients will be described, followed by examples of LHS projects using real EHR data that are still work in progress. From the initial results of these studies, I propose a new **"synthetic+real" strategy** to build small ML-LHS units: first simulate a ML-LHS with synthetic data and then apply the process to real EHR data. 

<br>

# 5. ML-enabled LHS Simulation

With the new synthetic patient technologies, it is now possible to synthesize patient records for a simulated EMR, and then simulate ML-LHS using the synthetic data to explore the benefits of LHS. LHS simulation represents an efficient way to develop ML algorithms and LHS processes, which can be applied to real patient data for building ML-LHS units. Because synthetic patient data based on public data has no privacy concerns, LHS simulation serves as an vehicle for sharing data and collaborating on algorithm development across organizations in large scale. This simulation step can potentially save a lot of time in the overall LHS project schedules.    

We conducted the first simulation study of ML-enabled LHS using synthetic patients generated by the Synthea technology, which has been published in [Nature Scientific Reports](https://www.nature.com/articles/s41598-022-23011-4) (Chen 2022). As a starting point, the study results are summarized below. 

## Basic design of ML-enabled LHS core unit

A simplified high-level design view of the ML-enabled LHS core unit for risk prediction task is shown in diagram. The design is focused on the two core ML steps for simulation: (1) build an initial ML model from existing EHR data, and (2) continuous ML with addition of new data to improve the ML model. This LHS design essentially utilizes the data-centric ML approach for EHR patient data. Therefore, the LHS process is primarily focused on increasing the quality and quantity of ML-usable data to improve risk prediction ML models. 

![design](img/Figure-1-simlhs-design.jpg)

Figure: High-level design of ML-enabled LHS core unit for risk prediction. The ML model is first built with initial patient data from EHRs. LHS learning cycles continuously use updated patient data to improve the ML model, and rapidly disseminate new model for doctors to use in making risk predictions.

## Simulation of ML-enabled LHS unit for lung cancer risk prediction

In order to simulate a lung cancer risk prediction LHS at a scale of a real-world hospital EHR containing 1 million patients, the LHS should have about 5,000 lung cancer patients. A total of 150,000 synthetic patients were synthesized by the [Synthea patient generator](https://github.com/synthetichealth/synthea), of which ~5,500 had lung cancer. Over 175 million points of data were available from over 13 million encounters for these Synthea patients, including 8 million diagnoses, 111 million observations, 24 million procedures and 15 million medications.

The continuous learning and improving process of ML-LHS was simulated by adding a 30,000 Synthea patient dataset to the previous updated dataset in 4 separate instances. A new XGBoost model was built for each updated dataset. As the size of dataset increased from 30,000 patients to 150,000 patients, the prediction performance of lung cancer recall increased from 0.849 to 0.936, the precision from 0.944 to 0.962, the AUC from 0.913 to 0.962, and the accuracy from 0.938 to 0.975. XGBoost base model was compared to the Random Forest (RF), Support Vector Machines (SVM), and K-Nearest Neighbors (KNN) base models. XGBoost models of Synthea patients had the best performance for lung cancer risk prediction.

![design](img/Figure-4-lc-ml-updates.png)

Figure: Continuous improvement of lung cancer risk prediction ML models with dataset size increase over time. Comparing algorithms: XGBoost, RF, SVM, and KNN. Recall was used as the key performance measure for risk prediction in preventive screening. Initial dataset: 30K patients; 4 data updates, each with 30K patients. 


## Verification of the LHS process with stroke disease target

To verify the effectiveness of the new data-centric ML-enabled LHS established in this study, the same LHS process should be able to develop risk prediction models for any target disease such as stroke and with similar performance: high recall and precision after the same number of data update iterations. 

Stroke occurred in Synthea patients more frequently than lung cancer. There were about 4,000 stroke patients in each of the 30K-patient datasets. The performance metrics improved with each data update. In the fourth cycle of learning and improvement, the updated pt150k dataset had about 20,000 stroke patients and the XGBoost base model’s key metrics increased to 0.908 recall, 0.964 precision, 0.948 AUC and 0.969 accuracy. 

The stroke model results confirmed that the established LHS process was similarly effective in building high-performance models for stroke risk prediction. We expect that this LHS process will be applicable to other diseases as well. 

![design](img/Figure-6-stroke-ml-updates.png)

Figure: Continuous improvement of XGBoost base models for stroke risk prediction with dataset size increase over time. Model performance was measured by recall, precision and AUC. The recall of the baseline model with 10 variables is shown as reference.  

## Conclusions of ML-LHS simulation study

This simulation study created the first synthetic ML-LHS unit and demonstrated its effectiveness in building risk prediction XGBoost base models from existing EHR data for target diseases such as lung cancer and stroke. With its intrinsically data-centric approach, the ML-LHS can continuously learn from new patient data over time to improve the ML model performance. 

The synthetic ML-LHS process can be applied to build disease risk prediction LHS with real patient data. In addition, real data ML models can also be optimized further by hyperparameter tuning.

NOTE: The ML models in LHS simulation are for research use only and not for real health care use.  

## ML-LHS Hypotheses

Based on the LHS simulation study, I have formulated two hypotheses: 

1. With data-centric approach, ML-LHS unit can ultimately achieve high recall and precision (>95%) for risk prediction of most diseases. 

2. Small community and rural clinics may not have enough data to build ML models by themselves, but can join clinical research networks (CRN) led by big hospitals so that the ML-LHS run in CRN can include clinics in learning cycles and thus enable clinics with the same ML/AI tools.

<br>

# 6. ML-enabled LHS Project Examples

ML-enabled LHS holds great promises in transforming health care and public health to more effective and efficient systems. I want to emphasize one particular application area here, which is dear to my heart: health equity. 

## Promising solution to global health care disparities 

As hypothesized above, ML-LHS has the potential to reduce health care disparities in rural and underprivileged populations. Although rural clinics and small urban community health centers (CHC) do not have sufficient numbers of patients required for building high-accuracy ML models for various tasks by themselves, the ML-enabled LHS design can be expanded to include all participants in clinical research networks (CRN-LHS). With CRNs, the teaching or tertiary hospitals are responsible to build ML models using data including those from the patient populations served by the rural clinics and urban CHCs. The resulting ML models and AI tools are rapidly disseminated among all providers within the LHS so that the clinics and CHCs are also enabled by the same ML/AI tools as the big hospitals. I expect that the CRN-LHS design not only offers a promising solution to reduce health care disparities in underserved populations but also prevent the small providers from leaving further behind by the healthcare AI revolution. 

## Challenges

The concept of ML-LHS is promising but also facing big challenges. Since LHS simultaneously involves system-level research and clinical practices, requirements for the initial ML models are significantly higher and may not be met by most reported ML models using EHR data. Moreover, because patient data cannot be shared openly for privacy reason, there is a lack of open access to patient datasets needed for developing ML-enabled LHS. As a result, it is difficult for wide-spread LHS research to occur in the emerging LHS field. 

Since I was invited to participate in the [2012 National Learning Health System Summit](https://www.learninghealth.org/kanter-summit), I have not yet seen any reports on ML-enabled LHS implementation within hospital clinical workflows that has the key desired LHS characteristics, such as automatic data collection, continuous machine learning, and rapid dissemination of new knowledge and best practices. Although some studies have reported successful applications of LHS concepts in hospital quality improvement, these use cases did not employ continuous machine learning of EHR data. (Bravata 2020, Horwitz 2019)


## New strategy for building ML-LHS

Because of the challenges, the LHS community needs to find new ways to facilitate research and implementation of ML-LHS. The LHS simulation study described above is an attempt to see how synthetic data could help hospitals and other types of health organizations to get started on exploring ML-LHS easier. 

For example, after seeing the results from the lung cancer risk prediction ML-LHS simulation, a clinical team at Guilin Medical University Affiliated Hospital has used the simulation process to train researchers and students and then developed a ML pipeline using real EHR data to build ML models for predicting risk of several diseases. This team is in the process of creating clinical research networks for implementation of ML-enabled LHS for disease early detections. More information will be shared here after this project makes progress toward running the ML-enabled LHS.

From the initial effect of synthetic data simulation on hospital's initiation of ML-LHS research projects, a new strategy is emerging: "synthetic+real" strategy. It breaks down a difficult task of building ML-LHS into two stages: 

1. In the first stage, simulate the ML core of ML-LHS using synthetic data, including data pipeline, ML algorithms, and team training. If this process works smoothly, it will give the clinical team more confidence of pursuing ML-LHS.

2. In the second stage, apply the process to real EHR data for data collection, model development, and clinical validation. Implement any other processes needed to run the learning cycles  that are embedded in the routine clinical workflow.


## Call for ML-LHS examples

The LHS field needs successful examples of ML-enabled LHS to demonstrate ML-LHS can actually produce the benefits and values to patients. If you have a project developing ml-enabled LHS, you may contact me at the [LHS Tech Forum Initiative](https://www.learninghealth.org/2020-lhs-technology-forum) of the Learning Health Community. We at the initiative are also reaching out to the global LHS community in order to collect examples of LHS projects, understand the challengs facing LHS research and implementation, and try to bring together innovators from industries and academics for conversations or collaborations. The initiative webpage will showcase some publications from successful LHS projects. This guide will also share example ML-LHS projects with information helpful to the global LHS community. 

In the following sections, you will find more detailed information on health data, synthetic patients, and data-driven machine learning, which are the key components of the learning cycles in ML-LHS. 

## ML-LHS Examples

[more to come …]

<br>
<br>

# 7. Health Data

## NAM reports
NAM 2010 report “Clinical Data as the Basic Staple of Health Learning: Creating and Protecting a Public Good: Workshop Summary” reviews the integration and use of electronic health records for knowledge development. It discusses efforts to investigate cutting-edge data-mining techniques for generating evidence on care practices and research. 

Examples of past projects presented in the report:

-	Nationwide Health Information Network (NHIN): Aggregated clinical data from multiple organizations.
-	[Cancer Biomedical Informatics Grid (caBIG)](https://biospecimens.cancer.gov/caBigTools.asp): It connected member systems of biomedical research and clinical trials, and provided shared data to the cancer research community. 

NAM 2013 report “Digital Data Improvement Priorities for Continuous Learning in Health and Health Care: Workshop Summary” explores the data quality issues and strategies central to the increasing capture and use of digital health data for knowledge development.

The increased collection and sharing of health data is quickly moving health care into the era of “big data.” Digital health data are produced in a variety of different environments:

-	EHRs containing data from routine care.
-	Data originating directly from patients.
-	Employers often possessing data on employees’ health care utilization, basic health status, and associated expenses.
-	Population health data routinely collected through the public health system and its surveys and surveillance activities.
-	Ongoing and completed clinical trial data.

Although the collection of large amounts of health and health-related data holds promise for both the scale and types of learning possible, data alone are not sufficient for learning. Sharing, aggregation, analysis, and the continuous management and improvement of these data are necessary to enable the transition to a continuously learning health system.

-	Innovative methods: Need development of methods using EHRs as a data source and performing observational studies on big data. Need development, validation, and use of predictive models to inform health-data uses, including risk interpretation by individuals.

-	Distributed approaches: Given the importance of privacy and security in the collection and use of patient health data, need to further develop and pilot the policies, analytic methods, and technologies associated with the use of distributed network approaches. 

    -	Example distributed data network: Mini-Sentinel (FDA-sponsored pilot initiative): A distributed dataset of >100 million people, supporting active safety surveillance of medical products.

## EHR data contents

Using [MIMIC-IV hospital data](https://mimic.mit.edu/docs/iv/modules/hosp/) as example: Information includes patient and admission details (patients,admissions,transfers), laboratory measurements (labevents, d_labitems), microbiology cultures (microbiologyevents), provider orders (poe, poe_detail), medication administration (emar, emar_detail), medication prescription (prescriptions, pharmacy), hospital billing information (diagnoses_icd, d_icd_diagnoses, procedures_icd, d_icd_procedures, hcpcsevents, d_hcpcs, drgcodes), and service related information (services).


## Open health data
There are some organizations sharing patient health data, which require permissions for necessary patient data protection. But, the lack of patient data access for developers to develop code seriously hinders learning health system innovations.  

EHR data sharing:

-   [MIT MIMIC-IV hospital datasets](https://mimic.mit.edu/docs/iv/): 

MIMIC-IV is a relational database containing real hospital stays for patients admitted to a tertiary academic medical center in Boston, MA, USA. MIMIC-IV contains comprehensive information for each patient while they were in the hospital: laboratory measurements, medications administered, vital signs documented, and so on. The database is intended to support a wide variety of research in healthcare.

-	[MIT MIMIC III ICU datasets](https://mimic.mit.edu/docs/iii/): 

MIMIC-III (Medical Information Mart for Intensive Care III) is a large, freely-available database comprising deidentified health-related data associated with over forty thousand patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012. The database includes information such as demographics, vital sign measurements made at the bedside (~1 data point per hour), laboratory test results, procedures, medications, caregiver notes, imaging reports, and mortality (both in and out of hospital).

-   [UK Clinical Practice Research Datalink (CPRD)](https://cprd.com/): 

CPRD is a real-world research service supporting retrospective and prospective public health and clinical studies. CPRD collects anonymized patient data from a network of GP practices across the UK. The data encompass 60 million patients, including 16 million currently registered patients.

-   [PhysioNet](https://physionet.org/about/database/): 

The PhysioNet Resource’s original and ongoing missions were to conduct and catalyze for biomedical research and education, in part by offering free access to large collections of physiological and clinical data and related open-source software.

Clinical research data sharing:

-	[Clinical trials data](https://clinicaltrials.gov/): ClinicalTrials.gov is a database of privately and publicly funded clinical studies conducted around the world.
-	[Vivli](https://vivli.org/): A global clinical research data sharing platform 

Health data sources:

-	[US Government health data](https://healthdata.gov/)
-	[ONC Health IT data](https://www.healthit.gov/data)
-	[CMS data](https://resdac.org/)
-	[NIH All-of-Us Research Program](https://allofus.nih.gov/)
-	[NIH National Center for Data to Health (CD2H)](https://cd2h.org/)
-	[NIH N3C data enclave](https://covid.cd2h.org/)
-	[NIH NCI cancer data](https://seer.cancer.gov/data-software/) 
-	[Harvard Dataverse](https://dataverse.harvard.edu/)
-	[Harvard DBMI NLP datasets](https://portal.dbmi.hms.harvard.edu/)
-   [Mendeley Data repository](https://data.mendeley.com/)

<br>

# 8. Synthetic Patient Data

Because real patient data are protected, it is critical to have synthetic patient data available for research and development. Complete synthetic patient data should be free of any privacy concern. For example, Synthea synthetic patients are synthesized from public data and thus Synthea data recently become widely used in developing and testing new health care information processes. 

## Synthea Synthetic Patients 

[Synthea](https://synthetichealth.github.io/synthea/) is an open-source, synthetic patient generator that models the medical history of synthetic patients. It generates high-quality, synthetic, realistic but not real, patient data, which is free from cost, privacy, and security restrictions. It enables research with patient data that is otherwise legally or practically unavailable. (Walonoski 2018).

A set of 1M Synthea synthetic patient medical records are available for download from Synthea developer Mitre Corp, a non-profit organization, at https://synthea.mitre.org/downloads.

### Synthea software:
[Synthea source code](https://github.com/synthetichealth/synthea) is available on github. Following its instructions, you can run Synthea software to create synthetic patient data. Design and more information are on [Synthea wiki](https://github.com/synthetichealth/synthea/wiki). 

### Software design:
Synthea system generates synthetic patient records using an agent-based approach. Each synthetic patient is generated independently, as they progress from birth to death through modular representations of various diseases and conditions. Each patient runs through every disease module in the system. 

Synthea disease modules are based on a [Generic Module Framework](https://github.com/synthetichealth/synthea/wiki/Generic-Module-Framework) that creates state machines representing the progression and standards of care for common diseases, using a set of predefined states, transitions, and conditional logic. Modules are built based on publicly available health data, including disease incidence and prevalence statistics, and clinical practice guidelines.

**Covered diseases:**

Synthea currently has over 90 different modules, each modeling a disease or condition. The module builder page lists the currently supported disease modules. The [Module Gallery](https://github.com/synthetichealth/synthea/wiki/Module-Gallery) lists some common modules.
 
**Table: Synthea top diseases and conditions.**

Top 10 Reasons Patients Visit PCP |	Top 10 Years of Life Lost |
----------------------------------|----------------------------
Routine infant/child health check |	Ischemic Heart Disease
Essential Hypertension |	Lung Cancer
Diabetes Mellitus |	Alzheimer’s Disease
Normal Pregnancy |	COPD
Respiratory Infections (Pharyngitis, Bronchitis, Sinusitis)	|Cerebrovascular Disease
General Adult Medical Examination |	Road Injuries
Disorders of Lipoid Metabolism	| Self-Harm
Ear Infections (Otitis Media) |	Diabetes Mellitus
Asthma	| Colorectal Cancer
Urinary Tract Infections |	Drug Use Disorders (limited to Opioids)

<br> 

### Extensibility
The beauty of Synthea’s module design is that you can add new modules to cover the diseases and conditions you are interested but not yet included in the Synthea software. 

-	[Module Builder](https://synthetichealth.github.io/module-builder/)
-	[Module Builder Tutorial](https://github.com/synthetichealth/synthea/wiki/Module-Builder-Tutorial)

For a walk-through of a complete example, see the [Complete Example](https://github.com/synthetichealth/synthea/wiki/Generic-Module-Framework%3A-Complete-Example) page. 

### Validation
See published studies for external validation of Synthea patient data. (Chen 2019).

### Patient medical records
Synthea patient medical records can be in standard FHIR format or CSV format. For easier view of data elements in the records of different domains, see the [list of record csv files](https://github.com/synthetichealth/synthea/wiki/CSV-File-Data-Dictionary) and the data fields in each file.  

**Table: Synthea patient medical record files.**

File	|Description
--------|-----------
allergies.csv	|Patient allergy data.
careplans.csv	|Patient care plan data, including goals.
claims.csv	|Patient claim data.
claims_transactions.csv	|Transactions per line item per claim.
conditions.csv	|Patient conditions or diagnoses.
devices.csv	|Patient-affixed permanent and semi-permanent devices.
encounters.csv	|Patient encounter data.
imaging_studies.csv	|Patient imaging metadata.
immunizations.csv	|Patient immunization data.
medications.csv	|Patient medication data.
observations.csv	|Patient observations including vital signs and lab reports.
organizations.csv	|Provider organizations including hospitals.
patients.csv	|Patient demographic data.
payer_transitions.csv	|Payer Transition data (i.e. changes in health insurance).
payers.csv	|Payer organization data.
procedures.csv	|Patient procedure data including surgeries.
providers.csv	|Clinicians that provide patient care.
supplies.csv	|Supplies used in the provision of care.

<br>

## Open synthetic patient data

The Open LHS Project has started an [open synthetic patient data repository](https://github.com/lhs-open/synthetic-data) on GitHub, with links to additional datasets published in the Mendeley Data repository.

The same open patient data are also published in the Harvard Dataverse: [Synthetic Patient Data ML Dataverse](https://dataverse.harvard.edu/dataverse/synthetic-patient-ml).

## Other synthetic patient data

- MDClone:

[MDClone](https://www.mdclone.com/) platform can create complete synthetic data sets based on any original data cohort without risk of exposing patient privacy and with the ability to share information securely. Its synthetic data is non-reversible, artificially created data that replicates the statistical characteristics and correlations of real-world, raw data. Utilizing both discrete and non-discrete variables of interest, synthetic data does not contain identifiable information because it uses a statistical approach to create a brand new data set. MDClone is used by NIH N3C project to generate synthetic data sets from Covid-19 patients for wider research use.  

- UK CPRD synthetic data:

The Clinical Practice Research Datalink (CPRD) in the UK has used its primary care data to create high-fidelity synthetic datasets replicate the complex clinical relationships in real primary care patient data while protecting patient privacy. The [CPRD synthetic data](https://cprd.com/synthetic-data) can be used instead of real patient data for complex statistical analyses as well as machine learning and artificial intelligence research applications. Through integrating outlier analysis with graphical modelling and resampling, CPRD approach can achieve synthetic data sets that are not significantly different from original ground truth data in terms of feature distributions, feature dependencies, and sensitivity analysis statistics when inferring machine learning classifiers. CPRD synthetic datasets can be used for training purposes or to improve algorithms or machine learning workflows. (Tucker 2020).

- NCI Cancer synthetic data:

Based on the publicly available cancer registry data from the NCI Surveillance Epidemiology and End Results (SEER) program, Goncalves et al. generated and evaluated synthetic patient data for cancers. (Goncalves 2020)  

They compared the existing methodologies to generate synthetic electronic health records. For each method, the process is as follows: given a set of private and real EHR samples, fit a model, and then generate new synthetic EHR samples from the learned model. The results found that the Mixture of Product of Multinomials (MPoM) and the categorical latent Gaussian process (CLGP) method can provide synthetic EHR samples with the following two characteristics: 1) statistical properties of the synthetic data are equivalent to the ones in the private real data, and 2) private information leakage from the model is not significant. 

## Machine learning using synthetic patient data

An IBM group used 1M Synthea patients to build 2D patient pathway and conducted neural network CNN and RNN machine learning. The resulting model was able to predict 10 common diseases with 80-90% accuracy. (Sbodio 2021). This study used an open source [patient pathway extractor](https://github.com/Alvearie/patient_pathway_extractor) for turning Synthea records to data ready for machine learning. 

Using three synthetic data generators that apply classification and regression trees, parametric, and Bayesian network approaches, Rankin et al. generated synthetic data from 19 open health datasets. They trained common machine learning models with the synthetic data and real data separately, and then measured model performance using only independent real data sets. The results showed only small decreases in accuracy for models trained with synthetic data compared to models trained with real data. (Rankin 2020)

## Limitations

Synthea data are considered realistic but not real. They have proven useful in developing and testing ML methods or processes, but the differences between Synthea and real patient data determine where the ML models can be used. Several limitations are present in the Synthea data: the limited number of diseases, some data is biased toward certain patient populations, and some health factors such as symptoms are missing. Due to the differences, any ML model built from synthetic data cannot be used in an actual clinical setting. 

<br>

# 9. Data-centric ML

## Healthcare AI
NAM 2019 special report, “Artificial Intelligence in Health Care: The Hope, the Hype, the Promise, the Peril”, outlines the current and near-term AI solutions; highlights the challenges, limitations, and best practices for AI development, adoption, and maintenance; offers an overview of the legal and regulatory landscape for AI tools designed for health care application; prioritizes the need for equity, inclusion, and a human rights lens for this work; and outlines key considerations for moving forward. (NAM 2019, Matheny 2020). See webinar [video](https://nam.edu/event/webinar-artificial-intelligence-and-health-care/).

AI was proposed in 1950s and had gone through two “AI Winters”. The current resurgence of AI started around 2010 due to the success of machine learning and data science techniques as well as significant increases in computational storage and power. It has fueled the growth of huge consumer businesses like Google, Amazon, and Apple. In addition to the common machine learning techniques like gradient boosting, random forest, support vector machines, and artificial neural networks, deep learning systems based on various neural networks have led the AI development to a new high. 

AI is poised to make transformative and disruptive advances in health care. The following table lists some of the healthcare applications of machine learning in the report. 

**Table: Example applications of machine learning.**

User Group	|Applications|
------------|------------|
Patients and families	|Health monitoring
Patients and families	|Risk assessment
Patients and families	|Disease prevention and management
Clinician care teams	|Early detection, prediction, diagnostic tools
Clinician care teams	|Precision medicine
Public health	|Identification of individuals at risk
Public health	|Population health

<br>

However, few examples of AI deployment and use within the health care delivery exist, and there is sparse evidence for improved outcomes when AI tools are deployed. For example, within ML risk prediction models, the sizable literature on model development and validation is in stark contrast to the scant data describing successful clinical deployment of those models in health care settings. 

Nonetheless, the report describes a framework for evaluation, decision making, and adoption of clinical AI applications in health care delivery systems and hospitals. It emphasizes that **healthcare AI should be implemented and deployed in the context of learning health systems**. It maps how AI could be considered within the LHS for each of the 10 recommendation areas outlined in the NAM 2013 "Best Care at Lower Cost" report.  

Since LHS has research embedded in health care practice, it must design ML model deployment as an integral part of the system. I think this requirement is fundamentally different from the usual AI research, but it is in syn with the requirements of LHS. Increasing implementation of LHS will result in more actual ML/AI deployments in health care setting.

SOURCE: NAM 2019 special AI report.

## Data-centric ML

LHS has another crucial feature that I recognize and value: It is inherently a data-centric approach for building high-performance ML models. A data-centric focus is often lacking in current ML/AI research. However, recently it has been recognized that data-centric ML/AI is as important as model-centric ML/AI. 
 
In model-centric ML development, the dataset is typically fixed and the focus is on iterating the model architecture or training optimization to improve the benchmark performance. 

In contract, the data-centric ML focuses systematic methods to evaluate, synthesize, clean and annotate the data used to train and test the AI model, which may use turn-key model builders.

Since the end-goal of LHS is successful deployment of its ML models in actual care delivery, LHS with real data may need to combine both approaches in order to reach such a difficult goal. Future studies are necessary to determine the optimal strategies for combining the data-centric and algorithm-centric approaches for developing and deploying ML models in LHS. As a general recommendation, LHS researchers using real data should consider using data-centric ML with base models to get the LHS running first, then optimize the models by hyperparameter tuning or modifying the underlying algorithms.

The latest paper on Nature Machine Intelligence from Dr. James Zou’s lab at Stanford University discusses recent advances, best practices and resources for creating data flow for data-centric AI. (Liang 2022). The paper grew out of a Stanford HAI workshop on data-centric AI (see presentation [recordings](https://lnkd.in/giWuSJCS)).
 
In 2022 interview by MIT Management magazine, Dr. Andrew Ng described why it’s time for [data-centric artificial intelligence](https://mitsloan.mit.edu/ideas-made-to-matter/why-its-time-data-centric-artificial-intelligence). For more clear problem statements and proposed solutions, watch Dr. Ng’s [webinar](https://www.youtube.com/watch?v=06-AZXmwHjo) on data-centric AI. You may join data-centric AI movement led by Dr. Ng at https://datacentricai.org/.


## EMR-wide ML
EMR-wide ML refers to machine learning using all features and data available in EMRs unlike the traditional statistical modeling that limits the variables used to a small number. Because lots of EMR data are in unstructured form, EMR-wide ML usually employs NLP to extract and standardize data from text. 

In traditional machine learning on EHR data, patients are represented by models as a vector of attributes or features. This approach relies on experts’ ability to define the appropriate features and design the model’s structure. However, deep learning models can learn useful representations from raw or minimally-processed data, with minimal need for expert guidance. This happens through a sequence of layers, each employing a large number of simple linear and nonlinear transformations to map their corresponding inputs to a representation. This progress across layers results in a final representation in which the data points form distinguishable patterns. (Li 2020, Solares 2020).

Depending on the tasks, two broad groups of ML algorithms can be used to build prediction models:

1.	Common ML algorithms: gradient boosting (e.g. [XGBoost](https://xgboost.readthedocs.io/en/stable/)), Random forest (RF), support vector machines (SVM), . 

2.	Deep neural network algorithms (or [deep learning](https://healthitanalytics.com/features/what-is-deep-learning-and-how-will-it-change-healthcare)): artificial neural networks (ANN), convolutional neural networks (CNN), recurrent neural networks (RNN), Long Short Term Memory (LSTM), Generative Adversarial Networks (GAN), Gated Recurrent Unit (GRU), feedforward network (FFN) 

The following studies are some representative examples of EMR-wide ML:

- Using EHR patient data from a state health information exchange, a research group at Stanford Medical School built a XGBoost model for predicting 1-year risk of incident lung cancer with an area under the curve (AUC) of 0.881 (Wang 2019). 

- Researchers at Mount Sinai Health Systems have developed a novel unsupervised deep feature learning method to derive a general-purpose patient representation from 700,000 patients in EHR that facilitates clinical predictive modeling. The study performed evaluation using 76,214 test patients comprising 78 diseases from diverse clinical domains and temporal windows. The results significantly outperformed those achieved using representations based on raw EHR data and alternative feature learning strategies. (Miotto 2016).

- Using about 1.6 million patients and 57,000 clinical concepts, researchers at Mount Sinai created an unsupervised framework based on deep learning to process heterogeneous EHRs and derive patient representations that can efficiently and effectively enable patient stratification at scale. (Landi 2020). 

- Google Health researchers proposed a representation of patients’ entire raw EHR records, and demonstrated that deep learning methods using this representation are capable of accurately predicting multiple medical events from multiple centers without site-specific data harmonization. These models outperformed traditional, clinically-used predictive models in all cases. (Rajkomar 2018).

- Building on the Transformer architecture and starting with 8 million patient in UK CPRD, researchers at Oxford University has developed a model called BEHRT (i.e., BERT for EHR) for predicting the next most likely diseases in one’s future visits. By comparison, BEHRT outperformed the best deep EHR models in the literature by more than 8% (absolute improvement) in prediction of a range of more than 300 diseases. (Li 2020).

- In an exhaustive benchmarking evaluation study, deep learning models consistently outperformed all the other approaches on various clinical prediction tasks using the Medical Information Mart for Intensive Care III (MIMIC-III) datasets available publicly. (Purushotham 2018)

- There is a lack of prospective evaluation of ML models in clinical care delivery. Nature Digital Medicine 2022 published an example of model building plus clinical validation and monitoring. The process first identifies a clinical decision point that can benefit from risk prediction, and then uses EHR data to retrospectively build a 60-day ED visit prediction model for cancer patients at home. The process validates the model in a randomized prospective study and then embeds the model in clinical workflow and monitor its performance routinely. (Coombs 2022).

<br>

# 10. More LHS Project Examples

-	FDA Sentinel System

The [FDA Sentinel System](https://www.sentinelinitiative.org/) is a working example of a learning health system that is expanding with the potential to create a global learning health system that can support medical product safety assessments and other research. (Brown 2022).

-	Kaiser HCSRN

The [Health Care Systems Research Network](https://www.hcsrn.org/en/) (HCSRN, formerly HMORN) brings together the research centers from many of the nation's best and most innovative health care systems. Its mission is to improve individual and population health through research that connects the resources and capabilities of learning health care systems for all.

-	PCORnet PaTH Clinical Research Network

As a PCORnet member, [PaTH](https://www.pathnetwork.org/) researchers work with clinicians, patients, and other stakeholders to develop meaningful research questions that can be integrated in care delivery for real-world health data. PaTH network includes many hospitals such as Geisinger, Johns Hopkins, PennState, Ohio State, Temple, Pittsburg, UPMC, Michigan. 

-	PEDsnet LHS - Children’s health research network

[PEDSnet](https://pedsnet.org/) does research to improve the health and lives of children. It is a large, national community of hospitals and healthcare organizations, researchers and clinicians, and patients and families. This community works together to identify the most important research questions that can reduce children's suffering and support their healthy development. 

-	ASCO CancerLinQ

[CancerLinQ](https://cancerlinq.org/), a subsidiary of ASCO, is a mission-driven, non-profit health technology company with a goal of improving quality of care, improving health outcomes for all patients with cancer, and advancing evidence-based research. CancerLinQ has built a community of learning across different platforms, disciplines, and skillsets, to enable improvements in care that can reach patients everywhere. 

-	Stanford University Collaborative Health Outcomes Information Registry (CHOIR) project

[Stanford CHOIR network for pain management](https://choir.stanford.edu/) is the earliest open source, open standard, and highly flexible platform for a learning healthcare system to optimize care and advance real-world research discovery and innovation.

-	VA LHS for transient ischemic attack project 

The Protocol-Guided Rapid Evaluation of Veterans Experiencing New Transient Neurological Symptoms ([PREVENT](https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2770248)) intervention was designed to align with the learning health care system model. This trial was to evaluate a multicomponent QI intervention to improve the quality of transient ischemic attack (TIA) care. (Bravata 2020)

-	NYU Langone Health LHS Project 

At the Center for Healthcare Innovation and Delivery Science (CHIDS), the [randomized QI projects](https://med.nyu.edu/centers-programs/healthcare-innovation-delivery-science/delivery-system-redesign) were developed in collaboration with the frontline care providers and staff to ensure seamless implementation with no additional burden. They verified the system-level interventions by LHS are effective in improving care qualities. Webinar [Video](https://rethinkingclinicaltrials.org/news/march-6-2020-creating-a-learning-health-system-through-randomization-leora-horwitz-md-mhs/).  (Horwitz 2019).

<br>

# 11. Related Resources

## Research & Development
-	Stanford HAI: [Data-centric AI workshop](https://hai.stanford.edu/events/data-centric-ai-virtual-workshop)
-	[Data-centric AI](https://datacentricai.org/)
-	Data-centric AI [Benchmark](https://www.datacentricai.cc/benchmark/)

## Healthcare
-	[PCORI LHS support](https://www.pcori.org/research-results/2017/supporting-next-generation-learning-health-systems-researchers) 

## Communities
-	[Learning Health Community](https://www.learninghealth.org/)
-   [LHS Tech Forum Initiative](https://www.learninghealth.org/2020-lhs-technology-forum) at Learning Health Community
-	[Learning Health Community](https://www.learninghealth.org/)
-	[The Learning Healthcare Project](https://learninghealthcareproject.org/)
-	[DCI Network](https://www.dcinetwork.org/about-us) at Harvard Medical School 

## Education
-	[Learning Health Systems](https://onlinelibrary.wiley.com/journal/23796146) journal 
-	[Department of Learning Health Sciences](https://medicine.umich.edu/dept/lhs/education) at University of Michigan
-	[Center for Learning Health System](https://celehs.hms.harvard.edu/index.html) at Harvard University 

## Policies
-	NAM: [The Learning Health System Series]( https://nam.edu/programs/value-science-driven-health-care/learning-health-system-series/).
-	AHRQ: [Learning Health Systems](https://www.ahrq.gov/learning-health-systems/index.html)

<br>

# References

- Abraham, E., C. Blanco, C. Castillo Lee, J. B. et al. 2016. Generating Knowledge from Best Care: Advancing the Continuously Learning Health System. NAM Perspectives. Discussion Paper, National Academy of Medicine, Washington, DC. https://doi.org/10.31478/201609b

- Balas, E, and S Boren. 2000. Managing clinical knowledge for healthcare improvements. In Yearbook of Medical Informatics, edited by V Schatauer. Stuttgart, Germany: Schattauer Publishing.

- Bravata DM, Myers LJ, Perkins AJ, et al. Assessment of the Protocol-Guided Rapid Evaluation of Veterans Experiencing New Transient Neurological Symptoms (PREVENT) Program for Improving Quality of Care for Transient Ischemic Attack: A Nonrandomized Cluster Trial. JAMA Netw Open. 3(9), e2015920 (2020). doi:10.1001/jamanetworkopen.2020.15920

- Brown JS, et al. The US Food and Drug Administration Sentinel System: a national resource for a learning health system, JAMIA, 2022; ocac153, https://doi.org/10.1093/jamia/ocac153.

- Chen, A., Chen, D.O. Simulation of a machine learning enabled learning health system for risk prediction using synthetic patient data. Sci Rep 12, 17917 (2022). https://doi.org/10.1038/s41598-022-23011-4

- Chen J, Chun D, Patel M, Chiang E, James J. The validity of synthetic clinical data: a validation study of a leading synthetic data generator (Synthea) using clinical quality measures. BMC Med Inform Decis Mak. 2019;19(1):44. doi: 10.1186/s12911-019-0793-0. 

- Coombs, L., Orlando, A., Wang, X. et al. A machine learning framework supporting prospective clinical decisions applied to risk prediction in oncology. npj Digit. Med. 5, 117 (2022). https://doi.org/10.1038/s41746-022-00660-3

- Friedman CP, Wong AK, Blumenthal D. Achieving a nationwide learning health system. Sci Transl Med. 2010 Nov 10;2(57):57cm29. doi: 10.1126/scitranslmed.3001456. PMID: 21068440.

- Goncalves, A., Ray, P., Soper, B. et al. Generation and evaluation of synthetic patient data. BMC Med Res Methodol 20, 108 (2020). https://doi.org/10.1186/s12874-020-00977-1.

- Horwitz LI, Kuznetsova M, Jones SA. Creating a Learning Health System through Rapid-Cycle, Randomized Testing. N Engl J Med. 2019 Sep 19;381(12):1175-1179. doi: 10.1056/NEJMsb1900856. https://www.nejm.org/doi/full/10.1056/NEJMsb1900856

- Institute of Medicine. 2001. Crossing the Quality Chasm: A New Health System for the 21st Century. Washington, DC: The National Academies Press. https://doi.org/10.17226/10027.

- Institute of Medicine. 2007. The Learning Healthcare System: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/11903.

- Institute of Medicine. 2010. Clinical Data as the Basic Staple of Health Learning: Creating and Protecting a Public Good: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/12212.

- Institute of Medicine. 2011. Digital Infrastructure for the Learning Health System: The Foundation for Continuous Improvement in Health and Health Care: Workshop Series Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/12912.

- Institute of Medicine and National Academy of Engineering. 2011. Engineering a Learning Healthcare System: A Look at the Future: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/12213.

- Institute of Medicine. 2013. Best Care at Lower Cost: The Path to Continuously Learning Health Care in America. Washington, DC: The National Academies Press. https://doi.org/10.17226/13444.

- Institute of Medicine. 2013. Observational Studies in a Learning Health System: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/18438.

- Institute of Medicine. 2013. Large Simple Trials and Knowledge Generation in a Learning Health System: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/18400.

- Institute of Medicine. 2013. Digital Data Improvement Priorities for Continuous Learning in Health and Health Care: Workshop Summary. Washington, DC: The National Academies Press. https://doi.org/10.17226/13424.

- Landi, I., Glicksberg, B.S., Lee, HC. et al. Deep representation learning of electronic health records to unlock patient stratification at scale. npj Digit. Med. 3, 96 (2020). https://doi.org/10.1038/s41746-020-0301-z

- Li, Y., Rao, S., Solares, J.R.A. et al. BEHRT: Transformer for Electronic Health Records. Sci Rep 10, 7155 (2020). https://doi.org/10.1038/s41598-020-62922-y.

- Liang, W., Tadesse, G.A., Ho, D. et al. Advances, challenges and opportunities in creating data for trustworthy AI. Nat Mach Intell (2022). https://doi.org/10.1038/s42256-022-00516-1

- Masoudi, F. A., E. P. Havranek, P. Wolfe, C. P. Gross, S. S. Rathore, J. F. Steiner, D. L. Ordin, and H. M. Krumholz. 2003. Most hospitalized older persons do not meet the enrolment criteria for clinical trials in heart failure. American Heart Journal. 146(2):250-257. https://doi.org/10.1016/S0002-8703(03)00189-3.

- Matheny ME, Whicher D, Thadaney Israni S. Artificial Intelligence in Health Care: A Report From the National Academy of Medicine. JAMA. 2020;323(6):509–510. doi:10.1001/jama.2019.21579. https://jamanetwork.com/journals/jama/article-abstract/2757958

- Miotto, R., Li, L., Kidd, B. et al. Deep Patient: An Unsupervised Representation to Predict the Future of Patients from the Electronic Health Records. Sci Rep 6, 26094 (2016). https://doi.org/10.1038/srep26094.

- NAM, 2019. “Artificial Intelligence in Health Care: The Hope, the Hype, the Promise, the Peril. A Special Publication from the National Academy of Medicine.” https://nam.edu/artificial-intelligence-special-publication/

- Purushotham S, et al. Benchmarking deep learning models on large healthcare datasets. J. Biomed. Inf. 2018; 83:112-134. Doi: 10.1016/j.jbi.2018.04.007.

- Rajkomar, A., Oren, E., Chen, K. et al. Scalable and accurate deep learning with electronic health records. npj Digital Med 1, 18 (2018). https://doi.org/10.1038/s41746-018-0029-1

- Rankin D, et al. Reliability of Supervised Machine Learning Using Synthetic Data in Health Care: Model to Preserve Privacy for Data Sharing. JMIR Med Inform. 2020 Jul 20;8(7):e18910. doi: 10.2196/18910. https://pubmed.ncbi.nlm.nih.gov/32501278/.

- Sbodio ML, Mulligan N, Speichert S, Lopez V, Bettencourt-Silva J. Encoding Health Records into Pathway Representations for Deep Learning. Stud Health Technol Inform. 2021;287:8-12. doi: 10.3233/SHTI210800. https://pubmed.ncbi.nlm.nih.gov/34795069/.

- Solares JRA, et al. Deep learning for electronic health records: A comparative review of multiple deep neural architectures. J Biomed Inform. 2020;101:103337. doi: 10.1016/j.jbi.2019.103337. PMID: 31916973.

- Tucker, A., Wang, Z., Rotalinti, Y. et al. Generating high-fidelity synthetic patient data for assessing machine learning healthcare software. npj Digit. Med. 3, 147 (2020).  https://doi.org/10.1038/s41746-020-00353-9.

- Walonoski J, et al. Synthea: An approach, method, and software mechanism for generating synthetic patients and the synthetic electronic health care record, JAMA, 2018, https://doi.org/10.1093/jamia/ocx079.

- Wang X, et al. Prediction of the 1-Year Risk of Incident Lung Cancer: Prospective Study Using Electronic Health Records from the State of Maine. J Med Internet Res 2019;21(5):e13260. doi: 10.2196/13260

---

<br>

## Acknowledgements

Thanks to Joshua C. Rubin, JD, MBA, MPH, MPP for reviewing and editing the guide. Special thanks to the NAM LHS report series. Thanks to all references cited.

Current Version: 20221103
  
