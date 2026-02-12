This project demonstrates a data-driven approach to learning an unknown probability density function (PDF) using a Generative Adversarial Network (GAN).
Instead of assuming any analytical or parametric distribution (such as Gaussian or exponential), the PDF is learned purely from data samples.

The experiment is conducted on real-world NO₂ (Nitrogen Dioxide) concentration data from India’s air quality dataset. A nonlinear transformation is applied to the original feature, and a GAN is trained to model the resulting distribution implicitly.

This project highlights the use of GANs beyond image generation, specifically for probability density estimation from raw data alone.

🎯 Objectives

Transform a real-world feature using a nonlinear function

Assume no prior knowledge of the resulting distribution

Train a GAN to learn the distribution only from samples

Generate synthetic samples from the trained generator

Approximate the learned PDF using Kernel Density Estimation (KDE)

Compare the real and learned distributions visually

📂 Dataset Description

Dataset: India Air Quality Data

Source: Kaggle

Feature Used: NO₂ (Nitrogen Dioxide concentration)

Reason for Choosing NO₂:

Continuous-valued real-world data

Non-Gaussian behavior

Suitable for density learning tasks

The code automatically handles:

Unknown CSV file names

Non-UTF8 file encodings

Inconsistent column naming (e.g., "NO2", "NO2 (µg/m3)", etc.)

🔄 Data Transformation

Each NO₂ value 
𝑥
x is transformed into a new variable 
𝑧
z using:

𝑧
=
𝑥
+
𝑎
𝑟
sin
⁡
(
𝑏
𝑟
𝑥
)
z=x+a
r
	​

sin(b
r
	​

x)

Where:

𝑎
𝑟
=
0.5
×
(
𝑟
 
m
o
d
 
7
)
a
r
	​

=0.5×(rmod7)
𝑏
𝑟
=
0.3
×
(
(
𝑟
 
m
o
d
 
5
)
+
1
)
b
r
	​

=0.3×((rmod5)+1)

𝑟
r is the university roll number

This nonlinear transformation ensures the resulting distribution has no known analytical form

🧠 Why GANs?

Traditional density estimation methods often assume:

A known distribution family

A fixed parametric form

In this task:

The distribution of 
𝑧
z is unknown

No parametric PDF is allowed

GANs solve this by:

Learning distributions implicitly

Using adversarial training instead of likelihood estimation

Generating samples that resemble the true data distribution

🏗️ GAN Architecture
Generator

Input: Gaussian noise 
∼
𝑁
(
0
,
1
)
∼N(0,1)
