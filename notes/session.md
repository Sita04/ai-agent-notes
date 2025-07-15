𝗔𝗜 𝗔𝗴𝗲𝗻𝘁𝘀 - 𝗪𝗵𝗮𝘁 𝗶𝘀 𝗮 𝗦𝗲𝘀𝘀𝗶𝗼𝗻 𝗦𝗲𝗿𝘃𝗶𝗰𝗲? 𝗗𝗼 𝘆𝗼𝘂 𝗻𝗲𝗲𝗱 𝗼𝗻𝗲?

If you are building a stateful AI agent, it most likely has two different types of memory: short-term and long-term. But why?

The answer lies in understanding the difference in problems you're solving: 𝗺𝗮𝗻𝗮𝗴𝗶𝗻𝗴 𝗮 𝗹𝗶𝘃𝗲 𝗰𝗼𝗻𝘃𝗲𝗿𝘀𝗮𝘁𝗶𝗼𝗻 vs 𝗯𝘂𝗶𝗹𝗱𝗶𝗻𝗴 𝗮 𝘀𝗲𝗮𝗿𝗰𝗵𝗮𝗯𝗹𝗲 𝗸𝗻𝗼𝘄𝗹𝗲𝗱𝗴𝗲 𝗮𝗿𝗰𝗵𝗶𝘃𝗲.

🧠 𝗦𝗲𝘀𝘀𝗶𝗼𝗻 𝗦𝗲𝗿𝘃𝗶𝗰𝗲 ~= 𝗥𝗔𝗠
This is your agent's short-term, working memory. Manages the immediate context of a single, active conversation. 

👉 Stores or fetches raw data - no cleanup 

👉 Bloated and contains information that's not needed in a long-term perspective.

👉 𝙴̲𝚡̲𝚊̲𝚖̲𝚙̲𝚕̲𝚎̲:̲ In the diagram below, you can see the sample Session data has grounding_metadata or custom_metadata, which may not add value to a long-term storage.

📚 𝗠𝗲𝗺𝗼𝗿𝘆 𝗦𝗲𝗿𝘃𝗶𝗰𝗲 ~= 𝗛𝗮𝗿𝗱 𝗗𝗿𝗶𝘃𝗲
This is your agent's long-term, searchable memory. It’s where your agent learns from past interactions across all conversations.

👉 Stores consolidated and relevant data only - prunes the rest

👉 Searches for info across all past conversations

👉 𝙴̲𝚡̲𝚊̲𝚖̲𝚙̲𝚕̲𝚎̲:̲ Its job is to ingest completed conversations and answer questions like, "What did we discuss about Project Alpha last week?"

Using a managed or long-term session service is non-negotiable for prod because it provides:
1) 𝚁̲𝚎̲𝚜̲𝚒̲𝚕̲𝚒̲𝚎̲𝚗̲𝚌̲𝚎̲:̲ If a server crashes, the conversation isn't lost.
2) 𝚂̲𝚌̲𝚊̲𝚕̲𝚊̲𝚋̲𝚒̲𝚕̲𝚒̲𝚝̲𝚢̲:̲ All instances of the agent can access a central source of truth to handle concurrent users.

📌 #AgentDevelopmentKit provides flexible options for both Session and Memory, including InMemory and Managed Services. Check out this code snippet to learn more: https://lnkd.in/giDNp33d

The overall session/ memory workflow is:
1️⃣ 𝗟𝗶𝘃𝗲: The Session Service manages the active conversation.

2️⃣ 𝗔𝗿𝗰𝗵𝗶𝘃𝗲: The conversation finishes. The completed session is sent to the Memory Service for learning.

3️⃣ 𝗖𝗼𝗻𝘀𝗼𝗹𝗶𝗱𝗮𝘁𝗲: The Memory service consolidates and stores only the relevant data.

4️⃣ 𝗤𝘂𝗲𝗿𝘆: When an agent sends a query later, the memory service searches its knowledge base and returns information.

5️⃣ 𝗣𝘂𝗿𝗴𝗲: The session data is deleted from the session database after a set TTL.

Here are some services you can use for managed implementations:

𝗙𝗼𝗿 𝗦𝗲𝘀𝘀𝗶𝗼𝗻 𝗠𝗮𝗻𝗮𝗴𝗲𝗺𝗲𝗻𝘁:
 ✅ VertexAISessionService: You can get started for free with Express mode: https://lnkd.in/gxiagQeY
 ✅ Databases: Redis, Postgres, MySQL, or any DB with the DatabaseSessionService.

𝗙𝗼𝗿 𝗠𝗲𝗺𝗼𝗿𝘆 𝗠𝗮𝗻𝗮𝗴𝗲𝗺𝗲𝗻𝘁:
 ✅ Vertex AI MemoryBank: https://lnkd.in/gNZcHQuS, mem0.ai
 ✅ Vector Databases