---
title: "Between Humans and Machines: Explainable Artificial Intelligence"
date: 2019-06-17T10:07:21+06:00
# post image
image: "images/blog/explainable-ai/Thumbnail.jpeg"
# post type (regular/featured)
type: "regular"
# meta description
description: "We need explainable Artificial Intelligence to avoid risks from malfunctioning systems."
# post draft
draft: false
---

We need explainable Artificial Intelligence to avoid risks from malfunctioning systems.

![Cover Image](../../images/blog/explainable-ai/cover.jpeg)

---

The recent crash of the Ethiopian Airlines aeroplane on 10th March 2019 in which all 157 people aboard died, raises some fundamental questions regarding technology. The pilot tried to raise the nose of the aircraft to gain height whereas the computer controlling the systems in the aircraft did not follow the command, but instead decided to lower the nose of the aircraft resulting in the crash of the aircraft. It will not be very far-fetched to say that the on-board computer refused to obey the command of the pilot to raise the nose of the aircraft which led to hitting the ground at high speed!

Let us understand the scenario. The computer is in the overall control of the aircraft. Pilot’s commands are viewed as inputs, perhaps as privileged inputs. However, it is the computer that takes the final decision about what to do and may not obey the commands of the pilot.

As technology becomes more complex, for example, the number of subsystems in aircraft increase with corresponding rise in their interactions, the controlling technology, also becomes more complex. Different elements of such a complex system become difficult to be controlled individually by a human being, so a computer is put there to actually control them.

The question is what should be done with the autonomous controls of such complex systems? Should a human override be provided? The answer is not simple as the next example illustrates.

### Nuclear Power Plant Accident

There was a major accident in a nuclear power plant in USA in 1979. Named as the Three Mile Island (TMI) accident, after the location of the power plant on Susquehanna river in Pennsylvania, it destroyed the reactor #2 of the power plant forever. Fortunately, it stopped short of a full meltdown of the reactor core, and a resulting bigger disaster. Its impact on the public mind was so great that no new nuclear power plants were built in USA after the accident!

28th March 1979 began as a usual day when the human operators of the power plant saw that the radioactivity from the plant was leaking out. On further investigation, they found that the cooling water contaminated with radiation was spilling into the adjoining building. The problem was that a pressure valve had broken down which caused the emergency water pumps to start automatically. It was an emergency measure taken by the system to avert a bigger more serious and catastrophic situation of nuclear meltdown.

The human action of shutting the pumps, eventually led to an explosion and partial meltdown of the core. It was sheer providence that the full meltdown did not occur. The plant was destroyed, and the remains are sealed and entombed in concrete even today. In the case of TMI, providing manual override proved to be a bigger problem, whereas not providing manual override in the other case led to the crash of the aircraft! So the question is what should be done?

### Artificial Intelligence Entering Our Lives

This question assumes a greater significance as Artificial Intelligence is set to enter our lives. It will be there ubiquitously all around us, controlling our systems and our lives. The so called Big Data and Machine Learning is driving it. It has the potential to create extremely complex and opaque systems. The promise is that it will give better performance than a system with human engineered knowledge or rules. However, the actions of such a system lie beyond the understanding of its own human designer.

The fear is how will it perform under some critical conditions? There are no guarantees given by the designer. Even a thorough testing may not uncover serious flaws. This means that even major flaws may remain hidden until a disaster strikes.

### Transparency

How do we approach the building of systems which will potentially deal with critical conditions? The answer lies in building transparent systems that lay bare their reasoning, and/or explain the reasoning behind their action. If the reasoning of the computer at the nuclear power plant was transparent, or the system could have explained when asked as to why it had started the backup pumps, the operator would not have shut them down. Even in the case of the Ethiopian Airlines, if the computer had the capability of explaining its actions, there might have been some alternative option before the pilot, though admittedly the time was short.

Transparent systems are explainable because by looking at their working, one can understand why and how they have arrived at a decision/action. Their working can be explained or understood by users/observers. A system capable of providing an explanation for its decision is a higher form of explainability, namely explainable by the self or self-explainability. The former (explainability) would be mandatory, the latter (self-explainability) would be desirable.

It turns out that explainablity also helps in improving the system. Once a particular weakness is identified in an explainable system, research can be done to improve it. In case of a modular system, the improvements are generally easier because they can be carried out selectively on specific modules. A good example is the design of automatic machine translation systems.

As systems continue to become complex, it will be even more necessary for them to explain what they have done, that is, not just laying bare their working, but to present their reasoning in terms the user can understand. It may also require user education, regarding the domain and the functioning of the system. This will allow dialogue to take place between the system and the user. The dialogue, for example, might first determine whether a common sense point has been missed. In the Ethiopean airliners case, the obvious common sense point would come out that the aeroplane is not losing speed and is in no danger of stalling. If the common sense points are accounted for, then one moves on to the next level of understanding. In the case of TMI accident, after there is agreement that radioactivity leak is there due to pumps, one goes to the reason why it should be allowed to continue even though it is dangerous, to prevent a bigger accident. The scenario is not unlike a set of experts discussing a common problem to arrive at the action to be undertaken. First, there is a discussion on the prevailing situation, to first arrive at agreement on facts about this situation. Second, there is discussion on reasons or causes which are responsible for the prevailing situation. The dialogue allows misunderstandings to be cleared. Finally, what should be done may be debated and the action decided upon. AI based systems would have to behave similarly. Transparency is discussed a lot in social systems, but simplicity is under-played today, in both technological systems as well as in social systems. There is a case for making AI systems simple as well as transparent, so that they are naturally explainable by observing their functioning. And finally the systems should become self-explaining, in other words, have the capability of self-explainability.

---

### Acknowledgements

<table style="width:50%; margin-right:50%;">
  <tr>
    <td align="center" >
      <img src="https://media-exp1.licdn.com/dms/image/C5603AQGvLJ9gjvEHbg/profile-displayphoto-shrink_400_400/0?e=1608163200&v=beta&t=qR6FZsRrKPB1_xx1wgIOBupf6krp0SbpEToY1P9wx0s" width="75px;" class="rounded-circle" style="margin-bottom: 0;"/>
      <br/><b>Author</b>
    </td>
    <td align="center" style="vertical-align: middle;"> <h4>
      Rajeev Sangal
      <br/>
      Director and Professor, IIIT-H
      <br/>
      <a href="https://www.linkedin.com/in/rajeev-sangal-7724b83b/" style="color: orange">LinkedIn</a>
    </h4></td>
  </tr>
</table>

(The author, an AI researcher working on Automatic Language Translation, is Professor at the Language Technologies Research Centre, IIIT Hyderabad. He was formerly Director, IIT(BHU), Varanasi and IIIT Hyderabad. Email: sangal@iiit.ac.in)

Appeared in: The Hindu, 2 June 2019, Opinion (Open Page). 

https://www.thehindu.com/opinion/open-page/between-humans-and-machines/article27399826.ece
