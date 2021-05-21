# Build Twitter

## Requirements clarification
- **Functional requirements**
   - Post: Users can post tweets.
      - Tweets can contain photos and videos.
   - Follow: Users can follow other users.
   - Timeline: System should be able to create and display a user’s timeline consisting of top tweets from all the people the user follows.
- **Non-functional requirements**
   - High availability.
   - Acceptable latency of generating timeline is 200ms.
   - High consistency is desirable (It should be ok for a user doesn’t see a tweet for a while).

## Estimation
- **Traffic estimation**
   - Our system will be read-heavy.
   - Users
      - 1 billion users. (Assumed)
      - 200 million daily active users. (Assumed)
      - 100 million new tweets every day. (Assumed)
      - Each user follows 200 people on average. (Assumed)
   - Number of tweets will be viewed per day
      - A user visits their timeline 2 times and visits five other people’s pages every day. (Assumed)
      - Each page has 20 tweets. (Assumed)
      - Number of tweets will be viewed per day = 200 million x ((2 + 5) x 20 tweets) = 28 billion
- **Storage estimation**
   - Types
      - Data: Yes
      - File: Yes
   - Capacity
      - Capacity for text
         - Each tweet 
            - Has 140 characters. (Assumed)
            - Need 30 bytes to store the metadata. (Assumed)
         - Each character needs 2 bytes.
         - Total size for storing new tweets per day = 100 million x (140 x 2 bytes + 30 bytes) = 30 GB
      - Capacity for photo and video
         - Every fifth tweet has a photo and every tenth has a video.
         - Photo size is 200 KB and Video size is 2 MB
         - Total size for storing new photos and videos per day = (100 million / 5 photos x 200 KB) + (100 million / 10 videos x 2MB) = 24 TB
- **Bandwidth estimation**