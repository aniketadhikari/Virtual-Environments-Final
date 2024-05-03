# Introduction
## Virtual environment
> **Virtual Environment (VE)**: a 3D, synthetic world or scene that is viewed interactively by a user #definition
- virtual environments (VEs) can provide users with a sense of *presence* (the feeling of “being there”—replacing the physical environment with the virtual one)
## Immersive virtual environment
> **Immersive Virtual Environment (IVE)**: A VE that surrounds the user in such a way that the user’s physical reality is <u>replaced</u> by the VE #definition
## Virtual reality
> **Virtual Reality**: set of technologies or a system used to produce a immersive virtual environment  OR the experience of using an immersive virtual environment #definition 
## Augmented reality
> **Augmented Reality** a 3D environment that combines real and virtual imagery, is interactive, and is registered #definition 
## Extended reality
> **Extended Reality** Any of the family of technologies that includes VR, AR, MR #definition 
## Mixed reality
> A set of approaches, including both VR and AR, in which real and virtual information is mixed in different combinations. #definition 
### MR Continuum
![[Pasted image 20240420160428.png]]
- A system’s position on the MR continuum indicates the mixture of virtuality and reality in the system (with the extremes being purely virtual and purely real). Mixed reality systems may move along this continuum as the user interacts with them (Milgram and Kishino 1994).
## Hype cycle
- What is meant to be observed here? #question
![[Pasted image 20240420164155.png]]
## Remaining barriers to XR adoption/usage #final 
### Problems that have been solved ✅
- technology driver
- application driver
- financial backing of Silicon Valley 
- Fitting into existing ecosystem of PC, game console, and smartphone 
- latency, rendering, modeling
### Problems remaining ❓
- All-day wearable XR glasses
	- battery life 👎
	- form factor 👎
	- FOV 👎
	- resolution 👎
- not very comfortable
- lack of general-purpose haptics
- not many applications beyond gaming with demonstrated usefulness for consumers 
- User experience
	> **UX**: A broader concept encompassing a user’s entire relationship with an artifact, including not only usability but also usefulness and emotional factors such as fun, joy, pride of ownership, and perceived elegance of design (Hartson and Pyla 2012). #definition 
	- Difficulty in evaluating 3D UIs often lead to low quality UX
# XR Systems and Components
## User-system loop #final 
![[Screenshot 2024-04-20 at 16.39.57.png]]
- user provides input through an input device (i.e. controller, mouse, or tracking device)
- through an input interpretation software, an input device communicates with the computer system
- computer system fetches model/data and sends in to the rendering software
- software is rendered on a display device 
- display device is viewed by user
## Process of producing graphics frames in an XR system
- tracking devices sense where the user's head position and orientation are at 
- software takes the tracking data and updates the head and eye position within the virtual environment 
- simulation system will update state of objects in the virtual world 
- rendering software renders the virtual environment from the POV of the eyes 
- images are presented on display device (i.e. HWD)
## Sources of 3D models for XR
- 3D models 
	- modeled by hand 
	- "captured" 
		- through laser scanning maybe
	- procedurally generated 
		- using AI and algorithms to dynamically create objects rather than manually
- Use of geometry, textures, materials, light sources, sound
- Animations have to be constructed
	- through keyframes or dynamically generated
- **Simulations**: rules for how the environment changes, evolves, responds #definition 
	- lighting models
	- physics model
	- object behavior models 
### AR Models
- With AR systems, there is a specific need to capture/generate 3D models of the real, physical world on the fly
- This means examining the real world in terms of its 
	- geometry
	- specific objects or object characteristics so as to render scenes with correct occlusion 
	- lighting
- Need to allow for virtual objects to be placed in *reasonable* real-world locations
## Scene graph
![[Pasted image 20240421180256.png]]
- nodes $\rightarrow$ objects 
- lines/edges $\rightarrow$ transformations
- serves as a hierarchical representation of the objects and elements within the virtual environment.
	- represent parent-child spatial relationships among objects for constraints and collision detection
	- developers can efficiently manage and manipulate elements within the application
	- We can decide which objects to render based on what is and isn't visible to the user 
- we want to avoid excessive position updates as this can be disorienting 
- Helps answer where certain things in the "world" are
	- Ex. where is left eye?
	- Ex. Where is chair1?
## Input degrees of freedom
![[Pasted image 20240421181618.png]]
> **degrees of freedom (DOF)**: number of independent dimensions of motion of a body. Can be used to describe the input possibilities provided by input devices, the motion of a complex articulated object such as a human arm and hand, or the possible movements of a virtual object #definition 
- with the head, there's about 6 degrees of freedom
	- left + right (roll)
	- up + down (yaw)
	- forward + back (pitch)
- need to ensure accurate head-tracking 
## Input latency
- too much latency in turning input into output of renderings can lead to cybersickness
## Smoothing and prediction for tracking data
- normally, most recent input is inserted into scene graph right before rendering
- to reduce latency between data being inserted and rendering, the tracking data can be smoothened or predicted by the system
## Simulation loop
- continuous updating and rendering of the virtual environment to maintain a consistent and interactive experience for the user.
- a simulation loop demands updates as quickly as possible to maintain a responsive and smooth XR experience
	- needs to be decoupled from tracking updates, event processing, rendering updates 
## Real-time rendering
- "frame rate"
- increased level of detail (LOD) 
	- assets require far more illustration and design
- **foveated rendering**: rendering only when in the view of the user to maintain performance #definition 
- **light-mapping**: brightness of a surface is pre-calculated and stored in texture maps for later use #definition 
- texture substitution
	- "imposters"
## Stereo rendering
[![Example view of HMD stereo rendering on an Oculus Rift CV1 using our... |  Download Scientific Diagram](https://www.researchgate.net/publication/332494154/figure/fig4/AS:748878013935616@1555557840653/Example-view-of-HMD-stereo-rendering-on-an-Oculus-Rift-CV1-using-our-method.jpg)
- used in computer graphics to create a three-dimensional perception of depth by simulating the way human eyes perceive images.
	- separate views for each eye
- mimicking the way objects are seen by the left and right eyes in reality
- requires inter-pupillary distance (IPD)
- requires 2x rendering since you render for left and right eye separately
	- can cut frame rate in half
## Visuomotor contingencies
- refer to the relationship between visual information (what is seen) and motor actions (what is done) in a given environment.
- how does what the user sees guide the way they act?
	- reach out and interact with it based on visual cues such as its size, shape, and spatial location.
- When the relationship between visual information and motor actions closely matches that of the real world, users experience a greater sense of presence and agency within the virtual environment.
# Human Factors & HCI
## Human factors
> **Human factors**: the capabilities, characteristics, and limitations of the human user #definition 
- applied psychological knowledge 
- This knowledge should inform design
- Historically applied in complex systems like aircrafts 
- How do humans process information? 
- How do humans perceive information? 
- What are their cognitive abilities and limitations?
- How do humans carry out actions?
## Perception/perceptual system #final 
- gathering information about the environment through senses

### vision 👀
- visual cues, such as depth information, helps the user interact with the application
	- specifically with actions like selection and manipulation
### audition 👂
- consists of outer, middle, and inner ear
- outer ear collects the sound and directs it to the eardrum, which vibrates, mimicking the sound waves it receives.
- **Binaural cues** arise from a comparison of the sound waves received by each ear.
- **Reverberation** is the collection of these reflected waves from various surfaces within a space and acts as an important acoustical cue for localizing sound sources.
- A sound’s intensity (which is perceived as **loudness**) is a primary cue for determining a sound source’s distance, because intensity will decrease as the distance to the source increases
### Somatosensory🖐
- haptics 
- related to touch and force
- force, pressure, temperature, texture
	- provide the human with information such as geometry, roughness (touch), and weight and inertia (force).
- **somatosensory**: what we feel when touching or grasping objects and how we perceive the location and movement of the parts of our bodies
### Olfaction 👃
* smell
* smell is especially well suited for danger detection
* olfactory cues have been shown to trigger emotional events or memories. 
* Both unconsciously and consciously, smells affect our emotions
### Gustation 👅
- taste
- Flavor can be influenced by a person’s expectations and satiety
### Proprioception / kinesthesis (position and movement of body parts 💪)
- Proprioceptive cues provide people with information about the position and angle of body joints, which humans are able to understand well without direct visual contact
	- even blind people are easily able to understand relative location and angle of hands and feet
- useful for many manipulation actions we perform, especially those that are performed out of sight
- active and passive
	- active kinesthetic cues are perceived when movement is self-induced
	- passive kinesthetic cues occur when the limbs are being moved by an external force
### Vestibular sense (balance ⚖)
- human balance system
	- orientation of body relative to gravity
	- movement of body through space (linear and rotational acceleration)
- provides cues for bodily motion
- influences cybersickness
## Parts of the eye related to visual perception
- lens $\rightarrow$ variable focus
- film $\rightarrow$ retina
	- determines the scene features such as light intensity and edges
	- distribution of *photoreceptors* (rods and cones) results in different abilities of the visual system in the center and the periphery 
	- central vision allows us to see colors, shapes, and text but this worsens towards the peripheral vision
	- photoreceptors convert light into electrical signals and send it to the brain
- amount of exposure $\rightarrow$ pupil
## Field of view
![[Pasted image 20240422151204.png]]
> refers to the maximum number of degrees of visual angle that can be seen instantaneously on a display #definition 
- display device's FOV must be $\le$ maximum FOV of human visual system
	- device can not expand our FOV past 180 degrees
- Frame of View $\ne$ Frame of Reference (FOR)
	- FOR refers the amount of physical space surrounding the user in which visual images are displayed
	- we can have 360 degrees of FOR
## Categories of 3D depth cues (static, dynamic, monocular, binocular, oculomotor)
### Static, monocular
> **static, monocular depth cues**: depth information can be inferred from a static image #definition 
- occlusion
	- **occlusion**: object closer to the user partially obstructs the view an object farther away
- relative size
- linear perspective 
	- parallel lines appear to converge as they move away from viewer
	- ![[Pasted image 20240422181511.png]]
- texture gradient
- aerial perspective
	- closer objects have more color saturation and brightness
- shading
- relative height to horizon
### Stereopsis (Static, binocular cue)
- each eye gets a slightly different image
- think about closing each eye
- only effective within a few feet of viewer
![[Pasted image 20240422182217.png]]
### Motion parallax
- dynamic, monocular cue 
- causes objects closer to viewer to move more quickly across the visual field objects farther away to move more slowly
### Oculomotor
> **oculomotor**: derived from muscular tension in the viewer's visual system #definition 
> **Accommodation**: physical stretching and relaxing of the eye lens caused by the eye muscles when focusing on an image #definition 
> **Vergence**: rotation of the viewer's eyes so images can be fused together at varying distances #definition
![[Pasted image 20240422182045.png]]
## Vergence-accommodation conflict
- standard stereo displays confuse the brain based on oculomotor cues 
- occurs when the brain receives mismatching cues between vergence and accommodation of the eye.
- The effect can be unpleasant and cause eye strain.
[![Vergence-accommodation conflict is a bitch — here's how to design around  it. | by Adrienne Hunter | VRINFLUX dot com | Medium](https://miro.medium.com/v2/resize:fit:1400/1*BRB4QLpT7bxA5QZN3d2xrA.jpeg)
## Cognitive load
- amount of cognitive work or effort required by a task or situation
## Spatial ability
- ability to judge distances or directions 
- ex. think of knowing directions to the nearest grocery store
## Spatial knowledge
- used for way-finding tasks 
- landmarks, routes, survey
- Ex. think of street signs and addresses 
## Fitts's Law
- there is always a trade-off between speed and accuracy
- "quick and accurate" is contradictory
## Human-computer interaction
> **HCI**: field that seeks to understand the relationship between human users and digital technological artifacts and to design new, effective ways for humans to use computer technologies for all sorts of purposes. #definition 

HCI is not simply about understanding our current interaction with computers. It is just as much, if not more, about designing new forms of interaction. This might take the form of developing a new input device or display, designing a set of gestures to be used in an application, or repurposing existing technology in imaginative new ways.
- H = single user, groups, I/O channels, memory, reasoning, problem solving
- C = interactive system with digital components, desktop, embedded system, input device, display device
- I = direct/indirect communication
## User interface
- the parts of a computer system that users see and interact with
- many practitioners of HCI have traditionally focused on user interfaces
- a small part of UX design
## User experience
- user interface 
- social context of the system
- ecology of tools and technologies in which the system lives 
- everything that the user brings to the table (training, cultural backgrounds, emotional state)
### Usability
- learnability
	- how quickly a novice user can comprehend the state of the system and determine what to do in order to complete a task
- effectiveness
	- completeness and accuracy with which users can achieve their intended goals. 
- efficiency
- productivity
- ease of use 
	- simplicity of a system from the user’s point of view and how much mental effort the user must exert every time to use the system
- retainability
	-  how well users maintain their knowledge of the system after not using it for a period of time
### Usefulness
-  capacity of a system to allow users to accomplish the goals of work or play.
- match of system/product to accomplishment of goals
- usefulness $\ne$ usability
	- A system can be highly usable  but if its function serves little purpose in a user’s life, it is not useful to that user.
### Emotional impact
- affective aspects of a user experience that influence the emotions of the user
- connects to feelings of user
	- fun, aesthetics, cool, elegant, pride of ownership
## Tradeoffs in HCI design
- design in HCI is a series of tradeoffs
- In making a design choice (and implicitly rejecting other choices), there are both benefits and disadvantages, and the benefits of one choice must be traded off against those of other choices.
- As a first principle of any sort of UX design (and of 3D UI design in particular), then, we encourage the reader to recognize these tradeoffs and then analyze them to determine the best course of action.
## HCI design principles
- simplicity
	- UI should be kept “as simple as possible and task focused
- structure
	- UI should be organized “in a meaningful and useful way”
- visibility
	- it should be obvious what a control accomplishes
- affordance
	- “it should be obvious how a control is used” 
- ergonomics
	-  science of fitting the job to the worker and the product to the user
- prevention
	- prevent user errors 
- automation
	- have the computer and UI automatically execute low-level actions that commonly occur as part of a high-level task 
- control
	- principle of ensuring that the computer and UI respond to the actions of the user
- feedback
	- it should be obvious when a control has been used
- error recovery
	- system should help the user recognize, diagnose, and recover from errors
	-  focused on helping the user after an error has already been committed.
- accessibility
	- interface is usable by all intended users, despite disabilities or environmental conditions 
- vocabulary 
	- use the vocabulary of the intended users NOT your own jargon or terminology
- recognition
	- UI should provide the knowledge required for operating the UI in the UI instead of requiring users to recall it from memory 
## Basic UX design process stages
### Design
- create interaction design concepts 
- generation of news ideas for exploration and inspiration
- critiquing designs
### Implement / Prototype
- realize design alternatives
### Evaluate
- verify and refine interaction design
- Goal is to provide feedback in software development in support of an iterative development process
- Recognize problems, understand underlying causes, and plan changes
### Analyze
- understand user work and needs
## Types of prototypes in HCI
### Paper prototypes 
- involve sketching designs on paper to represent the user interface and interactions of a product or system.
### Paper-in-device mockup
- Similar to paper prototypes, paper-in-device mockups involve sketching designs on paper, but they are placed within the physical frame of a device (such as a smartphone or tablet) to simulate the user experience more realistically.
- drawing on an iPad
### Click-through prototype
- Click-through prototypes are interactive prototypes that simulate the user interface and interactions of a digital product or system. They are typically created using prototyping tools or software.
- Figma
### Wizard of Oz prototype
- In a Wizard of Oz prototype, a human (the "wizard") manually simulates the behavior of a system behind the scenes while interacting with users as if the system were automated.
### Physical mockup 
- Physical mockups are three-dimensional models or prototypes of a product or system made from materials such as foam, wood, plastic, or clay.
### Animatic or video prototype
- Animatic or video prototypes use animations, motion graphics, or video footage to demonstrate the functionality and user experience of a product or system.
## Formative vs. summative evaluation
> **formative evaluation**: providing feedback and insights *during* the development process to improve the design, functionality, and user experience of a product or service. #definition
> **summative evaluation**: Summative evaluation aims to assess the overall effectiveness, impact, and outcomes of a completed product, service, or program at the *end* of the project #definition
## Qualitative vs. qualitative data
> **qualitative**: refers to non-numeric information that is descriptive in nature, often capturing qualities, characteristics, behaviors, opinions, or perceptions. #definition
> **quantitative**: refers to numeric information that can be measured and analyzed using statistical methods. It involves the collection of numerical data points and the use of mathematical or statistical techniques for analysis. #definition
## Objective vs. subjective data
> **objective**:  information that is based on observable and verifiable facts, without personal bias or interpretation. It is often quantifiable and measurable. #definition
> **subjective**: influenced by personal opinions, interpretations, feelings, or beliefs. It is based on individual experiences, perspectives, and judgments. #definition
# HWDs
## FOV vs. field of regard (FOR)
> **Field of View (FOV)**: refers to the maximum number of degrees of visual angle that can be seen in an instant on a display #definition
> **Field of Regard (FOR)**: refers to the amount of the physical space surrounding the user in which visual images are displayed #definition
- the FOV α is always less than or equal to the FOR β
- display device's FOV $\le$ maximum FOV of human visual system (180 degrees)
- Ex. FOV might be 50 degrees, but because the device is attached to the user’s head, with the display always in front of the user’s eyes, the FOR is 360 degrees. This is because the synthetic imagery is always perceived by the user regardless of her position or orientation
## Resolution
- related to pixel size and is a measure of visual quality
- resolution depends on 
	1) number of pixels 
		- more pixels $\rightarrow$ higher resolution
	2) screen size
	3) user's distance to display
		- the further the user is from the display, the higher the perceived resolution, because individual pixels are not distinguishable
- With large FOVs, resolution may not be constant across the display
	- Given a particular display panel, FOV trades off with resolution
## Pros and cons of HWDs compare to other XR displays #final 
### Pros
- 360-degree frame of reference 
	- display is always in view since it is strapped to the face
- low cost compared to large-scale immersive installations like the surround-screen displays
- don't require large amounts of space like the surround screen VR system with walls and a projector 
- each user has an their own, first-person POV
- portable, usable in various, arbitrary environments 
- capable of all 3D depth cues accept accommodation
- VR + AR capabilities 
### Cons
- ergonomics
	- can be heavy
	- uncomfortable
	- if it's tethered to a computer then it's even more annoying 
- visual isolation from the real world
	- putting on a HWD blinds you to the real world 
	- can't see obstacles a lot of times 
- accommodation-vergence mismatch
	- receiving mismatching cues on both eyes 
	-  Incorrect vergence response can cause double vision
### HWD design issues 
- optics
- low FOV compared to human's 180 FOV
- resolution
- inter-pupillary distance
- eye stain
- too heavy
- attachment
- tethering to a computer
- eye tracking and foveated rendering
## Video see-through vs. Optical see-through AR #final 
### Video See-Through
- with video see-through AR, there are cameras on the outside of the HWD
- streaming real-time video from head-mounted cameras to the graphics subsystem, which renders virtual computer graphics images into the video buffers in real time
	- blends the virtual and real.
- Wide FOVs are easier to support
- always of lower visual quality than a direct optical view. 
### Optical See-Through
- place optical combiners in front of the user’s eyes
- the combiners are partially transparent, so that the user can see the real world through them, and partially reflective, so that the user can see virtual images reflected from small head-mounted screens.
- provide a direct view of the real world with full resolution and no latency
- more common to see registration problems with the superimposed virtual imagery.
## Inter-pupillary distance (IPD)
> **IPD**: distance between the centers of the pupils of the two eyes. #definition 
[![Interpupillary Distance & Binoculars | Best Binocular Reviews](https://www.bestbinocularsreviews.com/blog/wp-content/uploads/2013/06/interpupillary-distance.jpg)
## Accommodation distance
> **Accommodation distance**: distance at which the display appears to be in focus to the viewer's eyes. In other words, it is the virtual distance at which the eyes need to accommodate (adjust focus) to perceive sharp imagery on the display. #definition 
- how far is the headset display from my eyes?
## Uses for eye tracking in HWDs
- Foveated rendering
	- determine where the user is looking (the foveal region) and allocate more rendering resources to that area, while reducing detail in the peripheral vision.
	- Helps improve performance by focusing computational resources where they are most needed, leading to more realistic and immersive visuals.
- Measures of engagement, workload, stress
	- analyzing metrics such as gaze duration, pupil dilation, and fixation patterns
	- assess how users interact with virtual content, how cognitively demanding tasks are, and how users respond emotionally to different stimuli.
- Explicit interaction
	- allowing users to control virtual objects or interfaces using their gaze.
	- Ex. Apple Vision Pro: gaze-and-pinch
- Implicit interaction
	- monitoring where users look and how their gaze behavior changes over time
	- systems can infer user intentions, preferences, and cognitive states
- Assessment of fixations or scan path
	- analyze where users look and how their gaze moves across a scene
	- can inform the design of AR and VR content, helping to optimize layouts, highlight important information, and minimize cognitive load.
- Providing avatar eye movements in collaborative environments
# Displays 
## Fish tank (monitor-based) VR #final 
> *stereo image of a three dimensional (3D) scene viewed on a monitor using a perspective projection coupled to the head position of the observer.* - Ware et. al (1993)
- conventional monitors, high-definition and higher resolution televisions, and front- or rear-projection displays using a wall or screen material as the projection surface
- single screen display coupled with stereo glasses are a simple yet effective visual display for 3D spatial applications
- relatively inexpensive ✅
- not very immersive ❌
- very limited range of movement ❌
	- due to FOR being severely limited to screen size
![[Pasted image 20240423170831.png]]
## Handheld mobile AR/VR #final 
- Relatively inexpensive 
- mobiles phones are already ubiquitous so adding AR to it is easy
- easy to facilitate social interaction 
- Easily portable
- Very easy to setup and use 
![[Pasted image 20240423171358.png]]
- Pokemon Go
## Surround-screen #final 
> **Surround-screen**: visual output device that increases the FOR for a user or group of users by incorporating either a set of display screens, a large curved display screen, or some combination of curved and planar screens that makes use of one or more light projection devices
- surround” the user with visual imagery in order to provide a large FOR
- surround-screen displays that make use of planar screen geometry. However, surround-screen displays also can utilize curved screens
![[Pasted image 20240423171527.png]]
- provides high spatial resolution and large FOR ✅
- large FOV, allowing user to utilize peripheral vision ✅
- provide monocular depth cues and motion parallax ✅
- expensive ❌
- require large amount of physical space ❌
- images are typically rendered from only one tracked user’s perspective, making it impossible to collaborate in the same space ❌
- users can have difficulty seeing objects in stereo under certain conditions
## Tiled displays #final 
![[Pasted image 20240423172018.png]]
![[Pasted image 20240423172008.png]]
## Volumetric displays #final 
> **volumetric displays**: permits the generation, absorption, or scattering of visible radiation from a set of localized and specified regions within a physical volume
- volumetric displays create “true” 3D images by actually illuminating points in 3D space. 
	- This is in contrast to other stereoscopic displays, which provide the illusion of 3D images but are actually projected onto a 2D surface.
![[Pasted image 20240424152804.png]]
![[Pasted image 20240424152958.png]]
## Projection mapping (Arbitrary surface displays), spatial AR #final 
- project imagery directly on arbitrary surfaces of any shape or size. 
- Creating visual displays out of everyday objects and surfaces
- difficult to deal with complexity of 
	- geometrical surface + color + texture
	- 3D stereo 
	- dealing with shadows 
	- display area restrictions 
- common to use 1 or more projector-camera pairs 
	- Using more than one projector helps to alleviate many issues due to shadows and display size.
![[Pasted image 20240424153442.png]]
![[Pasted image 20240424153124.png]]
## Types of haptic display (force feedback, tactile feedback, grasping force, ultrasonic)
### Force feedback #final 
- provides forces to users in response to their interactions with virtual or remote environments
- These displays typically use cables, tendons, and pulleys to transmit forces to the hand and fingers, with the actuators placed remotely.
![[Pasted image 20240424154659.png]]
![[Pasted image 20240424155044.png]]
### Tactile #final 
- aim to present haptic information by stimulating the user's tactile sense 
- Because human skin is highly sensitive, significantly less energy is required to produce strong and recognizable tactile sensations
- generally much smaller and more lightweight than the force displays
- applies physical stimuli on human skin
![[Pasted image 20240424155550.png]]
### Grasping force
- feedback provided to users when interacting with virtual or remote objects in a way that simulates the sensation of grasping and manipulating physical objects.
- designed to replicate the forces experienced when gripping objects in the real world
- may include force sensors, pressure sensors, or motion-tracking sensors that capture data about the user's hand position and the forces exerted during grasping.
![[Pasted image 20240424160002.png]]
![[Pasted image 20240424160054.png]]
### Ultrasonic
- powerful and directed sound waves a user can feel
- doesn't rely on physical contact with surfaces or actuators as the ultrasonic haptics can create tactile sensations in free space, 
	- no need for wearable devices or physical attachments 
- short effective distance
## Passive haptics / props #final
> **Passive Haptics**: passive physical representations of virtual objects (passive haptic devices) to communicate their physical qualities.
- Remember the paper I presented!
- Passive haptic devices (AKA props) are solid physical objects that directly mimic the virtual objects that they are used to represent.
- underlying limitation is their specificity and the need for exact registration between virtual objects and their passive representations
- Ex. a real cup or hammer can be used to provide a fully realistic haptic sensation when the virtual world contains a virtual cup or hammer
## Olfactory display 
![[Pasted image 20240424161238.png]]
## Vestibular display
![[Pasted image 20240424161314.png]]
- sense of self-motion and balance 
- "Displays" to these senses by:
	1. allowing actual body movement
	2. using motion platforms 
	3. stimulating certain parts of the brain
# Perception
## Cybersickness symptoms and theories
- AKA simulator sickness, or VR sickness
- Dizziness, nausea, disorientation, other bodily discomfort
- Symptoms similar to motion sickness
	- but not the same because cybersickness can occur without any motion
- Theories
	- sensory conflict, visual-vestibular mismatch
	- postural instability
	- poison theory
## Cybersickness mitigation
- Avoiding virtual accelerations (linear or rotational)
- reduce exposure time 
- Make purely virtual movements very fast and short duration (unnoticeable)
- Minimize latency
- Increase frame rate (60 fps)
- Keep users in control of movement 
### Novel Ideas
- include some physical motion rather than just motion in the virtual world
- reduce FOV during movement
- provide balance aids 
- provide a fixed visual reference frame 
## Distance misperception theories
- Distance is typically underestimated in HWDs 
	- Ex. reach out and fail to grab an object because it's farther than it actually is 
- Theories as to why distance misperception happens
	- FOV
		- If the FOV is narrow, users may not see peripheral objects or environmental cues that help judge distances accurately, leading to misinterpretations of depth.
	- presence
	- lack of visual detail
		- Lower-resolution displays or poor image quality can make it difficult for users to accurately judge distances between objects, leading to misinterpretations.
	- lack of virtual body
		- no hands in the virtual world
	- HWD ergonomics
	- accommodation-vergence conflict
		- stereoscopic displays may fail to show a single image and instead lead to double-vision
## Distance misperception mitigation
- practice, feedback
- interaction with the environment
- widening the FOV 
- adding an avatar of the user, self-avatar
- adding scale figures, objects familiar to the user 
- using a replica environment or transitional (pass-through?) environment
- peripheral light stimulation
## Depth perception issues in AR due to occlusion
- result of missing geometric model of the real-world environment 
- virtual content appears on top (or in front of) real content even when the real content is closer 
## Mitigation of depth perception in AR
- Simultaneous localization and mapping (SLAM) 
	- Creating a detailed 3D map of the environment using SLAM techniques enables AR systems to better understand the spatial layout of the surroundings
	- Info can be used to occlude virtual objects behind real-world objects more accurately.
- Implementing robust surface detection and tracking algorithms
	- helps AR systems recognize the geometry of real-world surfaces 
	- accurately detect surfaces like floors, walls, and tables
## Perceptual illusions
???
## Visual dominance
- Vision dominates our senses
	- contains the most information
	- largest % of the brain
	- when sensations conflict, vision wins out 
- especially true in VR as most of our other senses (olfactory, auditory, etc.) are limited or "silent"
- might contribute to problems with perception, but can also be used for beneficial purposes 
## Redirected walking
- problem: Area to use VR is very limited, especially for actions like walking or running
- possible solution: exploit visual dominance to give users the illusion that they are walking in a larger space when they're still in the same physical space. 
### Possible Approaches
- overt redirection near the boundary
- subtle redirection near the boundary
-  continuous redirection towards the center
- continuous redirection towards an orbit
## Haptic retargeting
- problem: difficult to achieve general-purpose haptics
- solution: exploit visual dominance to user a generic haptic prop to represent various virtual surfaces 
- solution 2: use a single haptic prop to represent multiple virtual objects by redirecting the user's reach
	- MY PAPER
## Pseudo haptics
- problem: some types of haptics can't be achieved with simple physical props due to things like force and weight
- possible solution: use visual dominance to stimulate haptics with visual movement 
## Place illusion
> **place illusion**: having a sensation of being in a real place
> **presence**: place illusion (PI) + plausibility illusion (Psi) 
## Body ownership illusion
- if...
	- a VR system produces a strong place illusion
	- and we see virtual body in the virtual environment
	- and if the virtual body responds to our movements in the way we expect it to
- then...
	- user takes ownership of the virtual body and treat it as their own
- Ex. body transfer illusion
# Tracking & Input
## Input device vs. interaction technique
- Input devices are just the physical tools that are used to implement various interaction techniques
- Many different interaction techniques can be mapped onto any given input device.
## Keyboards in VR
- traditional, keyboards are not conductive to immersive VR and mobile AR but it's still used
	- keyboards are bad because size of a traditional keyboard and the need for a supporting surface
	-  In the case of fully immersive 3D environments, when users are wearing an HWD, the real world is completely blocked out of the user’s view, making a traditional keyboard challenging to operate
![[keyboards-in-vr.png]]
- classic example of a traditional active sensing desktop input device that contains a set of discrete components (buttons)
- commonly used in many desktop 3D applications from modeling to computer games.
### solutions
- miniaturize keyboard
- reduce the number of keys
	- chord keyboard
- virtual keyboards
## Tablets/smartphones in VR/AR
- smaller device can be used in immersive VR, mobile, and AR settings
- pen and paper style interface
	- pen and tablet metaphor
- benefits
	- ubiquitous
	- on-board computing
	- networking capabilities
	- built-in display
- negatives
	- weight makes it unimmersive
![[tablet.png]]
## Isometric desktop 6-DOF input
- derivative of joystick
- uses isometric forces to collect 3D position and orientation data
	- push + pull for translation
	- twist + tilt for orientation
- moves objects dynamically in the three corresponding axes of x, y, z
- designed specifically for 3D desktop
	- commonly used in 3D applications for manipulating virtual objects.
- do not replace the mouse; rather, they are used in conjunction with it
	- One hand on the motion controller positions the objects in 3D space
	- other hand with the mouse can simultaneously select menu items and edit the object.
![[6-dof-movements.png]]
![[6-dof-input-device.png]]
## Tracking technologies and their pros/cons (mechanical, magnetic, inertial, optical, radar) #final 
### Mechanical Sensing 
- rigid structure 
- very accurate ✅
- low latency ✅
- bulky with limited range ❌ 
- often a component of haptic devices
- One end is fixed in place, while the other is attached to the object to be tracked (usually the user’s head or hand)
![[mechanical-sensing.png]]
### Magnetic Sensing
- uses a transmitting device that emits a low-frequency magnetic field 
- A small sensor (the receiver) determines its position and orientation relative to this magnetic source
- size of magnetic source determines tracking range
	- The smaller the magnetic source transmitter, the smaller the acceptable range of the tracking system. 
- Good accuracy that degrades as receiver moves away from the source ✅
- Limited range ❌
	- Doesn't work for outdoor or mobile AR
- Some metal objects distort the magnetic field ❌
![[Pasted image 20240501164142.png]]
### Inertial Sensing
- use a variety of inertial measurement devices, such as 
	- angular-rate gyroscopes
	- linear accelerometers
	- and magnetometers
- Typically, these sensors are combined into a single package called an inertial measurement unit (IMU).
- each device provides derivative measurements of position and orientation, so when combined the results are relative measurements
- tracking system is self-contained so the range is unlimited ✅
- produce data at high sampling rates ✅
- suffers from error accumulation from bias, noise, and drift ❌
- most inertial sensors are used only to track orientation ❌
![[interial-tracking.png]]
### Optical Sensing 
- use measurements of reflected or emitted light
- computer vision  + optical sensors
- many different types of cameras can be used
	- simple desktop webcams
	- stereo and depth cameras
	- high-res cameras with high sampling rates and pixel densities 
- have become more powerful and more common for 3D interaction
- inside-out or outside-in
	- direction from which tracking information is gathered relative to the AR system.
- marker-based or marker-less
	- approaches used in augmented reality (AR) systems to track the position and orientation of objects or users in the physical environment
- occlusion ❌
- complex ❌
- accuracy ❌
- untethered ✅
- depth cameras extract 3D representations of a user or environment
	- time of flight
	- structured light
	- stereo camera pair
### Radar Sensing
- uses modulated electromagnetic waves sent toward moving or static targets that scatters transmitted radiation, with some portion of the energy redirected back toward the radar where it is intercepted by a receiving antenna
- designed to detect large objects such as ships and aircraft where precise sensing is not required
	- impractical for sensing in 3D UIs
- not good at tracking small objects ❌
- tracks gestures with high accuracy ✅
-  subtle hand movements can be detected ✅
	- can lead to a wide variety of different interface controls for all facets of 3D selection and manipulation, navigation, and system control. 
- does not track hand/finger position or orientation ❌
## Inside-out vs. outside-in optical tracking
- direction from which tracking information is gathered relative to the AR system.
- inside-out refers to tracking from internal sensors 
- outside-out refers to tracking from external sensors 
## Marker-based vs. marker-less optical tracking
- marker based refers to the use of specific visual markers or fiducial markers placed within the environment 
- marker-less based refers to the capturing of the external environment without any markers 
## Different tracking #final 
### Marker-based inside-out systems
- use of internal sensors to track the environment from the perspective of the user
- requires the presence of specific visual markers or fiducial markers placed within the environment.
- device uses markers as reference points to track its own position and orientation relative to them.
- common in industrial applications or indoor navigation systems.
### Marker-less outside-in systems
- use external sensors, such as cameras or depth sensors, placed outside the user's device to track the environment.
- no need for markers 
- often used in experiences that require interaction with dynamic or unfamiliar environments, such as outdoor navigation or interactive gaming.
### Marker-based outside-in systems
- use of external sensors and markers around the environment
- commonly used where the environment may be dynamic or cluttered, but specific markers can still be placed strategically for tracking purposes, such as in indoor navigation systems or interactive exhibits.
### Marker-less inside-out systems
- rely solely on internal sensors to track the environment from the user's perspective.
- analyze the data from onboard sensors
- offer greater flexibility and portability
- commonly used in consumer-grade AR devices like smartphones, tablets, and mixed reality headsets, enabling applications such as mobile AR gaming, indoor navigation, and virtual try-on experiences.
## Hand tracking for XR (gloves, bare hand tracking)
- cornerstone of VR/AR
- Hand tracking as a whole ensures the hands are the primary mechanism for performing different 3D interaction tasks.
- can be done with both active and passive sensing
### Active
- active sensors involve placing trackers on areas that need tracking (ex. data gloves)
- large number of DOFs ✅
- needs calibration at times by users ❌
- user has to wear the device ❌
### Passive
- depth cameras extract finger position and millimeter wave radar can track moving fingers
- provide unobtrusive finger tracking ✅
- issues with line of sight ❌
- doesn't offer measurement range of data gloves ❌
## Eye tracking devices
- eye trackers are used to determine where user is looking 
	- Device tracks the user’s pupils using corneal reflections detected by a camera
- Used both as evaluation device and for interaction techniques 
	- i.e., gaze directed navigation and object selection
## 3D mice
- Handheld or user-worn input devices that combine position, orientation, and/or motion tracking with physical device components (buttons, sliders, etc.)
- Users physically move 3D mice in 3D space instead of just moving the device along a flat surface
![[3d-mice.png]]
# Fidelity & Presence
## Fidelity vs. presence
### Fidelity
> **fidelity**: how faithful a system is to the real world #definition 
- AKA immersion
### Presence
> **presence**: illusion of reality, the supposed human psychological response to the level of fidelity. #definition 
- the feeling of "being there"
- subjective impression, something that an individual feels
	- not controllable or directly measurable
- Slater's 2 dimensions of presence 
	1. place illusion (PI)
	2. plausibility (Psi)
- PI + Psi = Presence
## Place illusion (PI) #final 
> **place illusion**: illusion of being in a place in spite of the sure knowledge that you are not there #definition 
- do you feel like you're there?
## Plausibility illusion (Psi) #final 
> **plausibility illusion**: illusion that what is apparently happening is really happening (even though you know for sure that it is not) #definition 
- do you believe what you see?
## Embodiment #final 
- feeling of having a physical body within the virtual world
## Measures of presence (objective and subjective)
- simple rating scale
- questionnaires 
	- system usability scale (SUS)
	- prodromal questionnaire (PQ)
	- International Trauma Questionnaire (ITQ)
- psychological studies 
	- A-B comparisons
- psychological measures 
	- "duck test"
	- avatar social behaviors
- measure effects presence is hypothesized to mediate
## Scenario fidelity
> **scenario fidelity**: objective degree of exactness with which behaviors, rules, and object properties are reproduced in a simulation as compared to the real or intended experience #definition
- Level of detail in the environment and characters
## Display fidelity
> **display fidelity**: objective degree of exactness with which real-world sensory stimuli are reproduced by a display system #definition 
- immersion
- Resolution, FOV, refresh rate, sound quality, spatial audio
## Interaction fidelity
> **interaction fidelity**: objective degree of exactness with which real-world actions are reproduced in a simulation as compared to the real or intended experience
- naturalism
- Ability to perform actions that align with real-world movements
## Relationship between fidelity and effectiveness
- higher fidelity usually results in higher effectiveness 
- very few cases where higher fidelity is detrimental
- moderate fidelity can be bad
	- unfamiliar or not-quite-good-enough interface
## Uncanny valley of interaction fidelity
- applies to how users perceive the naturalness and effectiveness of interacting with virtual environments
- human-like features can elicit feelings of eeriness or discomfort
![[uncanny-valley-of-interaction-fidelity.png]]
- initially as interaction fidelity increases, user satisfaction or performance also increases.
- at a certain point, user satisfaction or performance can actually decrease because interactions might feel awkward, frustrating, or even creepy because they're not quite natural but not entirely artificial either.
- however, if interaction fidelity reaches a very high level, becoming indistinguishable from real-world interaction, user satisfaction and performance jump back up.
# Selection & Manipulation
## 3D interaction
> human-computer interaction in which the user's tasks are carried out in a 3D spatial context #definition 
- 3D input devices or 2D input devices with direct mappings to 3D 
## 3D user interface
- UI involves 3D interaction
![[3d-ui-examples.png]]
## 3D interaction technique
- a method allowing a user to accomplish a task in a 3D UI
	- hardware + software + metaphors/components
- choosing the right input and output devices are not sufficient for an effective 3D UI
	- also need software and metaphors/components
## Selection
- acquiring or identifying an object or subset of objects 
## Manipulation
- any act of physically handling objects with your hands
- **positioning**: change object's 3D position
- **rotation**: changing object's 3D orientation
- **scaling**: uniformly changing the size of an object 
## Integrated vs. separated DOFs
### Integrated DOFs
- motion or behavior of one component is directly influenced by the motion of another component
- level of coupling or interconnectedness between the components of the system.
- Ex. VR Gaming with hand controllers where player's hands are integrated with the virtual environment. hand controllers' movements are tightly coupled with the actions and reactions within the VR environment.
### Separated DOFs
- components that operate more independently of each other.
- Each degree of freedom can be analyzed or manipulated without significant influence from other degrees of freedom.
- Ex. Mixed Reality (MR) with spatial mapping where user's movements and interactions are often separated from the environmental elements.
## Power grip vs. precision grip
### Power Grip
 - all translation and rotation operations are carried out by larger muscle groups of the user’s shoulder, elbow, and wrist
![[power-grip.png]]
### Precision Grip
- user can use smaller and faster muscle groups in the fingers
-  usually results in better user performance, particularly in 3D rotation tasks #final 
- reduces clutching, which happens when an object is released and then re-grasped in order to complete the task #final 
	- infinite amount of spatial rotation without the need for clutching.
![[precision-grip.png]]
## Isomorphic vs. non-isomorphic interaction techniques #final 
### Isomorphic 
- realistic
-  one-to-one correspondence between hand motions in the physical and virtual world
- supposed to be the most natural
- negatives:
	- sometimes impractical because of constraints in input devices ❌
	- often ineffective because of limitations of humans ❌
	- stop imitating real life - make a better reality! ❌
### Non-isomorphic
- magic 
- deviates significantly from strict realism
- can allow users to manipulate objects quite differently than in the physical world, while maintaining usability and performance
## Simple virtual hand
- direct mapping of the user’s hand motion to a virtual hand’s motion in a VE
- isomorphic since it directly simulates our interaction with everyday objects
- only objects within the area of the user's reach can be selected and manipulated ❌
	- must employ a travel technique for far away objects
![[simple-virtual-hand.png]]
## Arm extension (e.g., Go-Go)
- allows user to interactively change the length of the virtual arm
- improves upon simple virtual hand
- when hand is close to avatar, go-go works like simple virtual hand
- when user extends their hand beyond a predefined distance, the virtual hand grows
- allows users to both bring faraway objects near and move near objects farther away.
![[go-go.png]]
## Control-display ratio
> relationship between the physical movement or manipulation required by the user (control) and the corresponding change or response in the displayed interface elements (display) #definition 
- quantifies the relationship between the user's input and the system's output.
-  think about controller sensitivity in Minecraft
- high CD ratio $\rightarrow$ small movements lead to significant movement
- low CD ratio $\rightarrow$ large movements are needed for significant movement
## Ray-casting
- cast rays from the viewer's point of view or from a camera through each pixel on the screen and into the scene
- shape of the ray can be a short line segment attached to the user’s hand
- powerful selection technique ✅
- At medium range with moderately sized or large objects, ray-casting simplest and most efficient selection technique ✅
- bad for high precision of selection is required ❌
- sometimes used for gaze
## Volume-based pointing
- require the definition of a vector and a volume to determine what user wants to select and manipulate
- leverage the entire volume accessible to the user's hand or controller to define the selection.
- flashlight, aperture, sphere-casting
## Progressive refinement
- gradually reducing set of objects until one remains
- used to optimize the rendering and manipulation of complex 3D scenes
- Useful in cluttered, dynamic environments
# Travel
## Travel vs. wayfinding
## Walking in place
## Omnidirectional treadmills
## Steering techniques
## Selection-based travel
## Teleportation
## Manipulation-based travel
## Nonisomorphic rotation (e.g., head rotation amplification)
## Wayfinding cues (landmarks, maps, compasses, trails, breadcrumbs)
# System Control
## Symbolic input
## Adapted 2D menus
## 1-DOF menus
## 3D widgets
## Voice commands
## Gestural commands
## Gesture vs. posture
## Gesture elicitation
## Tangible user interfaces
## Multimodal interaction
# Design Principles
## Feedback compliance
## Temporal compliance/latency
## Feedback substitution
## Passive haptic feedback
## Constraints
## Bimanual interaction - role of dominant and non-dominant hand
## Simulating reality vs. real-world metaphors vs. magic techniques
# Evaluation
## XR evaluation methods
## System performance metrics
## Task performance metrics
## Speed-accuracy tradeoff
## Measuring presence, cybersickness, and user comfort
## Measuring user experience
## Unique characteristics of 3D UI evaluation
## Informed consent
## Within- vs. between-subjects designs
## Counterbalancing
## Hygiene issues
# Applications and Other Research Issues
## Killer app
## Telepresence, social XR
## Intelligent AR
## Long-term XR use