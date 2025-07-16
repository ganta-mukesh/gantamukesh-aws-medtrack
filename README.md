🩺 MediTrack – Personal Medical Tracker App
MediTrack is a Flask-based web application that helps users manage their personal medical records — including medications and documents — with seamless cloud synchronization and notification support via AWS services.

📦 Features
🔐 User Authentication: Register & login with password encryption using bcrypt.

💊 Medicine Tracking: Add, view, update, and delete your medicines.

📁 Document Management: Upload and manage medical documents securely.

☁️ MongoDB Atlas: Stores all application data securely in the cloud.

🟢 AWS DynamoDB: Syncs user, medicine, and document data for redundancy and integration.

📣 AWS SNS: Sends real-time notifications (e.g., user registration events).

🛠️ Tech Stack
Frontend: HTML5, CSS3, Bootstrap

Backend: Python 3, Flask

Database: MongoDB Atlas

Cloud Services: AWS DynamoDB, Amazon SNS

Others: Boto3, Certifi, Python-dotenv

📁 Project Structure
bash
Copy
Edit
meditrack/
│
├── static/                   # CSS/JS/Images
├── templates/               # HTML Templates (login.html, home.html, etc.)
├── uploads/                 # User uploaded documents
├── app.py                   # Main Flask app
├── requirements.txt         # All dependencies
├── .env                     # Environment variables (secret)
└── README.md                # This file
⚙️ Environment Setup
1. 🔐 Create .env File
Create a .env file in the project root:

ini
Copy
Edit
MONGO_URI=mongodb+srv://<your-username>:<your-password>@<cluster>.mongodb.net/<dbname>?retryWrites=true&w=majority
SECRET_KEY=your_flask_secret_key

# AWS Credentials
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=your_aws_region

# AWS Services
SNS_TOPIC_ARN=your_sns_topic_arn
DYNAMO_USERS_TABLE=users_table_name
DYNAMO_MEDICINES_TABLE=medicines_table_name
DYNAMO_DOCUMENTS_TABLE=documents_table_name
📦 Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
If boto3 is missing:

bash
Copy
Edit
pip install boto3
🚀 Run the App
bash
Copy
Edit
python app.py
Then open your browser and navigate to:

arduino
Copy
Edit
http://localhost:5000/
🧠 How It Works
User registers → data stored in MongoDB and synced to DynamoDB → SNS notification is triggered.

Medicine/documents are handled similarly — any inserts trigger a sync to DynamoDB.

SNS can be used to notify admins, log events, or integrate with downstream systems.

🧪 Example Use Cases
Feature	MongoDB	DynamoDB	SNS
Register user	✅	✅	✅
Add medicine	✅	✅	❌
Upload document	✅	✅	❌
Delete medicine/doc	✅	✅ (optional)	❌

🔐 Security Notes
Passwords are hashed using bcrypt.

MongoDB URI and AWS credentials are kept in .env.

HTTPS is recommended for deployment.

🚀 Future Improvements
Email or SMS alerts using AWS SNS.

Calendar integration for medicine schedules.

Health analytics dashboard (ML-based).

👨‍💻 Author
Ganta Mukesh
Project lead and full-stack developer
GitHub: @ganta-mukesh
