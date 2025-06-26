# Computer-Vision
📷 Camera Calibration Using DLT and Levenberg–Marquardt Optimization
This project implements a two-step camera calibration pipeline that estimates both intrinsic and extrinsic parameters of a camera using:

Direct Linear Transform (DLT) — a linear method to estimate the projection matrix.

Levenberg–Marquardt Optimization — a non-linear refinement method to minimize reprojection error.

Overview
Accurate camera calibration is essential for 3D reconstruction, augmented reality, and robotics. While DLT offers a fast closed-form solution, it is sensitive to noise and does not minimize geometric error. This implementation improves DLT with a second-stage optimization using the Levenberg–Marquardt algorithm.

Features
Synthetic 3D-to-2D point generation with Gaussian noise.

Matrix construction for DLT using Singular Value Decomposition (SVD).

Reprojection error calculation.

Refinement via non-linear least squares using scipy.optimize.least_squares.

Visualization of before and after optimization projections.

Quantitative error comparison.

Technologies Used
Python 3

NumPy

SciPy

Matplotlib

Project Structure
graphql
Copy
Edit
camera_calibration/
├── calibration.py         # Core DLT and optimization functions
├── visualize.py           # Plotting reprojection results
├── synthetic_data.py      # Synthetic 3D/2D point generation
├── main.py                # Entry point to run the pipeline
├── README.md              # Project documentation
└── requirements.txt       # Python dependencies
 Results
Method	Mean Reprojection Error
DLT (Initial Estimate)	2.13 pixels
After LM Optimization	0.43 pixels

➡Nearly 5× improvement in accuracy after applying non-linear optimization.

 How to Run
Clone the repository:

bash
Copy
Edit
git clone https://github.com/SinUbyCosU/camera-calibration-dlt-lm.git
cd camera-calibration-dlt-lm
Install dependencies:

bash
Copy
Edit
pip install -r requirements.txt
Run the full pipeline:

bash
Copy
Edit
python main.py
📷 Sample Output
Red crosses: Projections using DLT

Blue circles: Ground-truth

After LM Optimization: Red crosses align closely with blue circles

📚 References
Szeliski, R. Computer Vision: Algorithms and Applications (2010)

Zhang, Z. A Flexible New Technique for Camera Calibration, IEEE PAMI (2000)

Hartley, R. & Zisserman, A. Multiple View Geometry in Computer Vision, 2nd ed.

