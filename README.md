# myapp-data
from datetime import datetime

print("Token Test")
print("-" * 10)
print("Repo:", github.repo)
print("Owner:", github.owner)
print("Time:", datetime.now())

text = f"Herzlichen Glückwunsch, {github.owner}!"
message = f"Token test"

# write test
print("\nWrite test:")
try:
    content_sha, commit_sha = github.write(
        filepath="test.json",
        content_bytes=text.encode("utf-8"),
        commit_message=message,
    )
    print(message, "... succeeded")
except Exception as e:
    print(message, "... failed:", e)

# read test
print("\nRead test:")
try:
    content, sha = github.read("test.json")
    print(message, "... succeeded") 
except Exception as e:
    print(message, "... failed:", e)

# content check test
print("\nContent check test:")
try:
    assert content.decode("utf-8") == text
    print(message, "... succeeded")
except Exception as e:
    print(message, "... failed:", e)
