# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Real-world recommendation systems combine content information about songs with behavioral signals such as plays, skips, likes, and playlists from many listeners. This simulation focuses on the content-based part: it compares a listener's stated taste profile with each song's attributes. It prioritizes genre and mood matches, then rewards songs whose energy is close to the listener's target and whose acousticness matches their preference. Each song receives a score, and the highest-scoring songs become the recommendations.

The simulation uses these features:

- `Song`:  `id`, `title`, `artist`, `genre`, `mood`, `energy`, `tempo_bpm`, `valence`, `danceability`, and `acousticness`.
- `UserProfile`: `favorite_genre`, `favorite_mood`, `target_energy`, and `likes_acoustic`.

### Algorithm Recipe

For every song, the recommender starts at 0 points. It adds 3 points for a matching genre and 2 points for a matching mood. It then rewards energy closeness with `2 * (1 - abs(song_energy - target_energy))`, so a song whose energy is closer to the target earns more points. Finally, it adds 1 point when the song's acousticness fits whether the listener likes acoustic music. After scoring every song, it sorts the songs from highest score to lowest score and returns the top five.

### Potential Biases

This system may over-prioritize genre and miss a great song from a different genre that has the right mood or energy. It also relies on a small catalog and simple labels, so genres and moods that have fewer songs will be less likely to appear in recommendations. Because it does not use listening behavior such as skips or saves, it cannot learn when a listener's taste changes.


---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

```
Loaded songs: 18

Top recommendations
========================================
1. Sunrise City — Neon Echo
   Score: 7.96
   Reasons:
   - genre match (+3.0)
   - mood match (+2.0)
   - energy close to target (+1.96)
   - acousticness matches preference (+1.0)

2. Gym Hero — Max Pulse
   Score: 5.74
   Reasons:
   - genre match (+3.0)
   - energy close to target (+1.74)
   - acousticness matches preference (+1.0)

3. Rooftop Lights — Indigo Parade
   Score: 4.92
   Reasons:
   - mood match (+2.0)
   - energy close to target (+1.92)
   - acousticness matches preference (+1.0)

4. Concrete Crown — Rhythm District
   Score: 2.94
   Reasons:
   - energy close to target (+1.94)
   - acousticness matches preference (+1.0)

5. Night Drive Loop — Neon Echo
   Score: 2.90
   Reasons:
   - energy close to target (+1.90)
   - acousticness matches preference (+1.0)
```

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this
