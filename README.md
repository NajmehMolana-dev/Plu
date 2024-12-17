import matplotlib.pyplot as plt

# Define Plutchik's Wheel of Emotions Data
primary_emotions = {
    "Joy": ["Serenity", "Joy", "Ecstasy"],
    "Trust": ["Acceptance", "Trust", "Admiration"],
    "Fear": ["Apprehension", "Fear", "Terror"],
    "Surprise": ["Distraction", "Surprise", "Amazement"],
    "Sadness": ["Pensiveness", "Sadness", "Grief"],
    "Disgust": ["Boredom", "Disgust", "Loathing"],
    "Anger": ["Annoyance", "Anger", "Rage"],
    "Anticipation": ["Interest", "Anticipation", "Vigilance"],
}

# Define Colors for Each Emotion
colors = {
    "Joy": "gold",
    "Trust": "green",
    "Fear": "darkgreen",
    "Surprise": "lightblue",
    "Sadness": "blue",
    "Disgust": "purple",
    "Anger": "red",
    "Anticipation": "orange",
}

# Create the Visualization
fig, ax = plt.subplots(figsize=(10, 10), subplot_kw=dict(polar=True))

# Number of Primary Emotions
num_emotions = len(primary_emotions)
angles = [n / float(num_emotions) * 2 * 3.14159 for n in range(num_emotions)]

# Plot Each Primary Emotion and Its Sublayers
for i, (emotion, layers) in enumerate(primary_emotions.items()):
    for j, layer in enumerate(layers):
        ax.bar(
            angles[i],
            (j + 1) * 1.5,  # Radius for each layer
            width=0.4,
            color=colors[emotion],
            alpha=0.3 if j == 0 else 0.6 if j == 1 else 1,
            edgecolor="black",
            label=emotion if j == 0 else "",
        )

# Adjust Labels and Titles
ax.set_xticks(angles)
ax.set_xticklabels(primary_emotions.keys(), fontsize=12)
ax.set_yticklabels([])
ax.set_title("Emotion Mapping Based on Plutchik's Wheel", fontsize=14)

# Add a Legend
handles = [plt.Line2D([0], [0], color=colors[e], lw=4, label=e) for e in primary_emotions]
ax.legend(handles=handles, loc="upper right", bbox_to_anchor=(1.3, 1.1))

plt.tight_layout()
plt.show()
