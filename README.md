from flask import Flask, request
from twilio.twiml.voice_response import VoiceResponse

app = Flask(__name__)

# Replace these values with your Twilio credentials
account_sid = 'your_account_sid'
auth_token = 'your_auth_token'
twilio_phone_number = 'your_twilio_phone_number'
destination_phone_number = 'your_destination_phone_number'

@app.route('/call', methods=['POST'])
def handle_call():
    # Get the incoming phone number
    caller_phone_number = request.form['From']

    # Create TwiML response to forward the call
    response = VoiceResponse()
    response.dial(destination_phone_number)

    return str(response)

if __name__ == "__main__":
    app.run(debug=True)
