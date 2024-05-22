const response = await openai.createChatCompletion({
  model:"gpt-3.5-turbo",
  messages:[
  {
  role:"system",
  content:"你扮演一名AI的專家",
  },
  temperature:0.7,
  max_tokes:64,
  });
  
