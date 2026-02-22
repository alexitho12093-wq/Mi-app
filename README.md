const express = require("express");
const crypto = require("crypto");
const rateLimit = require("express-rate-limit");
const helmet = require("helmet");
const cors = require("cors");

const app = express();

// Seguridad avanzada
app.use(helmet());
app.use(cors());
app.use(express.json());

// Protección contra spam y ataques
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
});
app.use(limiter);

// Sistema simple de encriptación
function encrypt(text) {
  return crypto.createHash("sha256").update(text).digest("hex");
}

// IA simulada avanzada
function artificialIntelligence(input) {
  if (input.includes("seguridad")) {
    return "Sistema seguro activado.";
  }
  if (input.includes("crear app")) {
    return "Te ayudo a crear una aplicación avanzada.";
  }
  return "Estoy aprendiendo... dame más información.";
}

// Ruta principal
app.get("/", (req, res) => {
  res.send("🔥 Servidor IA Potente Activo");
});

// Endpoint IA
app.post("/ai", (req, res) => {
  const userInput = req.body.message;
  const response = artificialIntelligence(userInput);
  res.json({
    encryptedUserMessage: encrypt(userInput),
    aiResponse: response,
  });
});

// Puerto
const PORT = 3000;
app.listen(PORT, () => {
  console.log(`🚀 Servidor corriendo en puerto ${PORT}`);
});
