from transformers import pipeline

# 使用預訓練的聊天模型
chatbot = pipeline("conversational", model="microsoft/DialoGPT-medium")

# 開始對話
while True:
    user_input = input("You: ")
    if user_input.lower() in ["exit", "quit"]:
        break
    
    # 將用戶輸入傳給聊天機器人
    response = chatbot(user_input)
    
    # 打印回應
    print(f"Bot: {response[0]['generated_text']}")
