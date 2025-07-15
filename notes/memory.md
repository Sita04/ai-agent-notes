𝗔𝗜 𝗔𝗴𝗲𝗻𝘁𝘀 - 𝗠𝗲𝗺𝗼𝗿𝘆 𝗟𝗮𝘆𝗲𝗿

When designing an AI agent, one of the most important architectural decisions is how to handle memory? The memory layer is responsible for persisting and retrieving information across sessions. 

Here are the 2 generic approaches:

✅ 𝗩𝗼𝗹𝗮𝘁𝗶𝗹𝗲 𝗠𝗲𝗺𝗼𝗿𝘆 (𝗜𝗻-𝗠𝗲𝗺𝗼𝗿𝘆): Best for development and local testing. Data is stored in the application's memory and is lost on restart.

✅ 𝗣𝗲𝗿𝘀𝗶𝘀𝘁𝗲𝗻𝘁 𝗠𝗲𝗺𝗼𝗿𝘆 (𝗗𝗮𝘁𝗮𝗯𝗮𝘀𝗲/𝗠𝗮𝗻𝗮𝗴𝗲𝗱 𝗦𝗲𝗿𝘃𝗶𝗰𝗲): Essential for production. This can be a managed service or a self-hosted database, ensuring context survives across interactions.

For developers using the hashtag#AgentDevelopmentKit (ADK), the framework provides various options to implement the above approaches:

1. 𝗣𝗿𝗼𝘁𝗼𝘁𝘆𝗽𝗶𝗻𝗴 (𝗜𝗻𝗠𝗲𝗺𝗼𝗿𝘆𝗠𝗲𝗺𝗼𝗿𝘆𝗦𝗲𝗿𝘃𝗶𝗰𝗲): The default, zero-setup option for local development where data persistence isn't required. 
2. 𝗠𝗮𝗻𝗮𝗴𝗲𝗱 𝗦𝗼𝗹𝘂𝘁𝗶𝗼𝗻 (𝗩𝗲𝗿𝘁𝗲𝘅𝗔𝗶𝗠𝗲𝗺𝗼𝗿𝘆𝗕𝗮𝗻𝗸𝗦𝗲𝗿𝘃𝗶𝗰𝗲): This is Google Cloud's native Memory-as-a-Service (MaaS). 
3. 𝗧𝗵𝗶𝗿𝗱-𝗣𝗮𝗿𝘁𝘆 𝗦𝗼𝗹𝘂𝘁𝗶𝗼𝗻𝘀: For maximum flexibility, you can integrate a wide range of external memory services, such as: 
 ✨ mem0.ai, the open-source MCP Toolbox for Databases, SurrealDB etc.,
4. 𝗖𝘂𝘀𝘁𝗼𝗺 𝗜𝗻𝘁𝗲𝗴𝗿𝗮𝘁𝗶𝗼𝗻: Write your own wrapper for any database or service to gain full control over your agent's memory architecture.

The core workflow is roughly:

👉 𝗦𝘁𝗲𝗽 𝟭: Initialize: 𝚖𝚎𝚖𝚘𝚛𝚢 = 𝚈𝚘𝚞𝚛𝙼𝚎𝚖𝚘𝚛𝚢𝚂𝚎𝚛𝚟𝚒𝚌𝚎()

👉 𝗦𝘁𝗲𝗽 𝟮: Add Session to Memory: 𝚖𝚎𝚖𝚘𝚛𝚢.𝚊𝚍𝚍_𝚜𝚎𝚜𝚜𝚒𝚘𝚗_𝚝𝚘_𝚖𝚎𝚖𝚘𝚛𝚢(𝚜𝚎𝚜𝚜𝚒𝚘𝚗)

👉 𝗦𝘁𝗲𝗽 𝟯: Provide Memory to Agent: 𝚛𝚞𝚗𝚗𝚎𝚛 = 𝚁𝚞𝚗𝚗𝚎𝚛(..., 𝚖𝚎𝚖𝚘𝚛𝚢_𝚜𝚎𝚛𝚟𝚒𝚌𝚎=𝚖𝚎𝚖𝚘𝚛𝚢)

👉 𝗦𝘁𝗲𝗽 𝟰: Search Memory to retrieve context as needed: 𝚛𝚎𝚜𝚞𝚕𝚝𝚜 = 𝚊𝚠𝚊𝚒𝚝 𝚌𝚘𝚗𝚝𝚎𝚡𝚝.𝚜𝚎𝚊𝚛𝚌𝚑_𝚖𝚎𝚖𝚘𝚛𝚢(𝚚𝚞𝚎𝚛𝚢)

Steps 2 and 3 will vary if you adopt a 3rd party solution or a custom integration. This modular approach allows you to start simple and scale to a production-grade memory solution.

𝗥𝗲𝘀𝗼𝘂𝗿𝗰𝗲𝘀:

 • ADK Memory docs: https://google.github.io/adk-docs/sessions/memory/

 • VertexAI MemoryBank: https://cloud.google.com/vertex-ai/generative-ai/docs/agent-engine/memory-bank/quickstart-adk

 • mem0.ai: https://docs.mem0.ai/integrations/google-ai-adk

 • Surreal DB: https://surrealdb.com/docs/integrations/frameworks/googleagent