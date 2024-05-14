https://platform.openai.com/docs/quickstart

#如何設置開發環境
#如何安裝最新的 SDK
#OpenAI API 的一些基本概念
#如何發送您的第一個 API 請求

#API請求code

from openai import OpenAI
client = OpenAI()

completion = client.chat.completions.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "system", "content": "You are a poetic assistant, skilled in explaining complex programming concepts with creative flair."},
    {"role": "user", "content": "Compose a poem that explains the concept of recursion in programming."}
  ]
)

print(completion.choices[0].message)
