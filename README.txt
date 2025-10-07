Chatbot de Evaluación de Desempeño en Telegram

Este proyecto es un bot automatizado de evaluaciones de desempeño, desarrollado con n8n, Telegram Bot API y MongoDB.
Su objetivo es permitir que los usuarios completen una evaluación de 5 preguntas directamente desde Telegram, almacenando los resultados en MongoDB y generando un feedback automático.

🚀 Características principales

✅ Inicio de evaluación manual mediante el comando /start

🔄 Evaluaciones automáticas programadas (vía Schedule Trigger)

🧠 Progreso de evaluación persistente por usuario (con sesiones activas en MongoDB)

💾 Almacenamiento estructurado de respuestas

📊 Cálculo automático de métricas y nivel de desempeño

📬 Envío de feedback personalizado al finalizar

📎 Consulta de resultados previos con /resultados

🛑 Validación de errores (si el usuario responde fuera del rango 1-5 o sin tener una sesión activa)

🌐 API para Dashboard (REST Webhook listo para consumir en front-end)

🧱 Estructura en MongoDB
🟢 Colección evaluation_sessions (sesiones activas)
{
  "_id": ObjectId("..."),
  "userId": "6216726733",
  "chatId": "6216726733",
  "username": "Usuario",
  "currentQuestion": 1,
  "answers": [],
  "questions": [
    { "id": 1, "category": "productividad", "text": "¿Qué tan satisfecho estás con tu nivel de productividad?" },
    { "id": 2, "category": "comunicacion", "text": "¿Cómo calificas la comunicación con tu equipo?" },
    { "id": 3, "category": "objetivos", "text": "¿En qué medida sientes que cumples tus objetivos?" },
    { "id": 4, "category": "crecimiento", "text": "¿Qué tan satisfecho estás con las oportunidades de crecimiento?" },
    { "id": 5, "category": "balance", "text": "¿Cómo evalúas tu balance trabajo-vida personal?" }
  ],
  "startedAt": "2025-10-06T01:03:16.551Z",
  "status": "active",
  "automated": false
}

🔵 Colección evaluation_results (evaluaciones completas)
{
  "_id": ObjectId("..."),
  "userId": "6216726733",
  "username": "Usuario",
  "metrics": {
    "totalScore": 21,
    "averageScore": 4.2,
    "percentage": 84,
    "performanceLevel": "Excelente"
  },
  "categoryScores": {
    "Productividad": 4,
    "Comunicación de Equipo": 5,
    "Cumplimiento de Objetivos": 4,
    "Oportunidades de Crecimiento": 4,
    "Balance Trabajo-Vida": 4
  },
  "feedback": "🌟 ¡Excelente desempeño!...",
  "completedAt": "2025-10-06T01:10:45.551Z"
}

📌 Comandos disponibles en el Bot
Comando	Descripción
/start	Inicia una nueva evaluación
/resultados	Muestra el último resultado guardado
(1 a 5)	Responde preguntas en medio de una evaluación
👨‍💻 Autor

Desarrollado por Alejandro Torres para Nolatech.
