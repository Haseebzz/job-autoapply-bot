FROM python:3.10-slim

# Install dependencies and Chromium + Chromedriver
RUN apt-get update && apt-get install -y \
    wget unzip curl gnupg ca-certificates \
    fonts-liberation libappindicator3-1 libasound2 \
    libnss3 libxss1 libxtst6 libx11-xcb1 libxcomposite1 \
    libxdamage1 libxrandr2 libatk1.0-0 libatk-bridge2.0-0 \
    libcups2 libgbm1 xdg-utils \
    chromium chromium-driver \
    && rm -rf /var/lib/apt/lists/*

# Set paths for Chrome and Chromedriver
ENV CHROME_BIN=/usr/bin/chromium
ENV CHROMEDRIVER_PATH=/usr/bin/chromedriver

# Set working directory and install Python deps
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy your app code 
COPY . /app 
WORKDIR /app

# Run the app
CMD ["python3", "main.py"]


