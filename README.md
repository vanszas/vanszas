import re
import sys

with open(r"C:\Users\ADMIN\.gemini\antigravity\brain\7f09aa8d-19ea-48b4-8568-9b4be0e9743e\.system_generated\steps\29\content.md", "r", encoding="utf-8") as f:
    html = f.read()

# Let's find some keywords or text content
text_content = re.sub('<[^<]+?>', ' ', html)
text_content = re.sub(r'\s+', ' ', text_content)

skills = ["Unity", "Blender", "Maya", "Photoshop", "Premiere", "After Effects", "C#", "C++", "Python", "Blueprint", "Unreal"]
found_skills = [s for s in skills if s.lower() in html.lower()]

links = re.findall(r'href="([^"]+)"', html)
unique_links = list(set(links))

with open(r"C:\Users\ADMIN\.gemini\antigravity\brain\7f09aa8d-19ea-48b4-8568-9b4be0e9743e\scratch\parsed_info.txt", "w", encoding="utf-8") as out:
    out.write("FOUND SKILLS: " + ", ".join(found_skills) + "\n\n")
    out.write("TEXT CONTENT PREVIEW:\n" + text_content[:4000] + "\n\n")
    out.write("LINKS:\n" + "\n".join(unique_links) + "\n")
print("Done writing to parsed_info.txt")
