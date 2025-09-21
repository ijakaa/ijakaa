#!/bin/bash
# GitHub Profile README Generator with Stats

# === CONFIG ===
USERNAME="ijakaa"   # <-- your GitHub username
TITLE="👋 Hi, I'm ijakaa!"
BIO="Welcome to my GitHub profile!  
I'm passionate about building robust web and mobile applications using **PHP**, **MySQL**, **Laravel**, and **Flutter**."

TECH_STACK_BACKEND=("PHP" "Laravel" "MySQL")
TECH_STACK_MOBILE=("Flutter (Dart)")
PROJECTS=(
  "Amazons|https://github.com/|A project built with a focus on delivering high-impact solutions."
  "Wema Sacco|https://github.com/|A Laravel-based application for streamlined cooperative management."
  "RentEase App|https://github.com/ijakaa/|A Flutter-powered platform making property rental easy and intuitive."
)
FUNFACT="When I’m not coding, you might find me exploring new tech trends, brainstorming startup ideas, or enjoying a good book."

# === SCRIPT ===
README="README.md"

# Start README
cat > $README <<EOF
# $TITLE

$BIO

---

## 🚀 About Me

- 💻 **Tech Stack:**  
  - Backend: $(IFS=,; echo "**${TECH_STACK_BACKEND[*]}**")  
  - Mobile: $(IFS=,; echo "**${TECH_STACK_MOBILE[*]}**")
- 🌱 Always learning new ways to craft seamless, scalable, and secure digital solutions.
- 🎯 Obsessed with clean code, performance, and elegant user experiences.

---

## 🏆 Featured Projects
EOF

# Add projects
for project in "${PROJECTS[@]}"; do
  NAME=$(echo "$project" | cut -d'|' -f1)
  LINK=$(echo "$project" | cut -d'|' -f2)
  DESC=$(echo "$project" | cut -d'|' -f3)
  echo -e "\n- [**$NAME**]($LINK)  \n  _$DESC_" >> $README
done

cat >> $README <<EOF

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=$USERNAME&show_icons=true&theme=radical" alt="$USERNAME's GitHub stats" height="180px"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=$USERNAME&layout=compact&theme=radical" alt="Top Languages" height="180px"/>
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=$USERNAME&theme=radical" alt="GitHub Streak"/>
</p>

---

## 📫 Connect With Me

- GitHub: [$USERNAME](https://github.com/$USERNAME)
<!-- Add more links below if you want, e.g., LinkedIn, Website, Twitter -->

---

## ⚡ Fun Fact

$FUNFACT

---

_Thanks for stopping by!_  
⭐️ _Feel free to check out my repositories and connect_
EOF

# Git commit & push
git add $README
git commit -m "chore: update profile README with stats"
git push origin main

echo "✅ Profile README with stats generated and pushed!"
!_
