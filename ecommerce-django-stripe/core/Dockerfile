FROM python:3.9-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Used by Stripe for callback URL 
# for successful payment and cancelled
ENV SERVER_ADDRESS http://localhost:5085/

# Stripe Secrets 
# ENV STRIPE_SECRET_KEY      <YOUR_STRIPE_SECRET_KEY>
# ENV STRIPE_PUBLISHABLE_KEY <YOUR_STRIPE_PUBLISHABLE_KEY>

COPY requirements.txt .

# Install python dependencies
RUN pip install --upgrade pip && pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

# Gunicorn to run the app
CMD ["gunicorn", "-b", "0.0.0.0:8000", "run:app"]
