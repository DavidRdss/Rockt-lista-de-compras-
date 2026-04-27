# Rockt-lista-de-compras-
Desenvolver o Quicklist, uma aplicação simples para gerenciar a lista de compras da semana. O usuário poderá adicionar novos itens, marcar como concluídos e também remover da lista quando não forem mais necessários. Além disso, a interface deve ser responsiva, funcionando tanto em desktop quanto em mobile, com feedback visual para ações realizadas.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Quicklist</title>
  <link rel="stylesheet" href="style.css" />
  <script src="script.js" defer></script>
</head>
<body>
  <main class="app">
    <header class="topbar">
      <a href="#" class="back-button" aria-label="Voltar">
        ← Voltar
      </a>
      <p class="brand">Quicklist</p>
    </header>

    <section class="card">
      <p class="eyebrow">Lista de compras da semana</p>
      <h1>Organize suas compras de forma simples</h1>
      <p class="description">
        Adicione itens, marque o que já foi comprado e remova o que não precisa mais.
      </p>

      <form id="item-form" class="form">
        <input
          type="text"
          id="item-input"
          placeholder="Adicionar novo item"
          aria-label="Adicionar novo item"
        />
        <button type="submit" class="add-button">Adicionar item</button>
      </form>

      <p id="error-message" class="error-message" aria-live="polite"></p>

      <ul id="shopping-list" class="shopping-list" aria-label="Lista de compras">
        <li class="shopping-item">
          <label class="item-check">
            <input type="checkbox" />
            <span class="item-text">Arroz</span>
          </label>
          <button class="remove-button" aria-label="Remover Arroz">🗑️</button>
        </li>

        <li class="shopping-item">
          <label class="item-check">
            <input type="checkbox" />
            <span class="item-text">Feijão</span>
          </label>
          <button class="remove-button" aria-label="Remover Feijão">🗑️</button>
        </li>

        <li class="shopping-item">
          <label class="item-check">
            <input type="checkbox" />
            <span class="item-text">Leite</span>
          </label>
          <button class="remove-button" aria-label="Remover Leite">🗑️</button>
        </li>

        <li class="shopping-item">
          <label class="item-check">
            <input type="checkbox" />
            <span class="item-text">Pão</span>
          </label>
          <button class="remove-button" aria-label="Remover Pão">🗑️</button>
        </li>
      </ul>
    </section>
  </main>

  <div id="toast" class="toast" role="status" aria-live="polite"></div>
</body>
</html>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --bg: #f4f4f4;
  --card: #ffffff;
  --text: #1f1f1f;
  --muted: #6b7280;
  --primary: #5b5bd6;
  --primary-dark: #4747b7;
  --border: #e5e7eb;
  --danger: #e5484d;
  --success: #1f9d55;
  --shadow: 0 16px 40px rgba(0, 0, 0, 0.08);
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
}

.app {
  width: 100%;
  max-width: 760px;
  margin: 0 auto;
  padding: 24px;
}

.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}

.back-button {
  text-decoration: none;
  color: var(--primary);
  font-weight: 700;
  background: transparent;
  border: 1px solid transparent;
  padding: 10px 12px;
  border-radius: 12px;
}

.back-button:hover {
  background: rgba(91, 91, 214, 0.08);
}

.brand {
  font-weight: 800;
  color: var(--muted);
  letter-spacing: 0.04em;
  text-transform: uppercase;
  font-size: 0.9rem;
}

.card {
  background: var(--card);
  border-radius: 24px;
  box-shadow: var(--shadow);
  padding: 28px;
}

.eyebrow {
  color: var(--primary);
  font-size: 0.9rem;
  font-weight: 700;
  text-transform: uppercase;
  margin-bottom: 10px;
}

h1 {
  font-size: 2rem;
  line-height: 1.15;
  margin-bottom: 12px;
}

.description {
  color: var(--muted);
  margin-bottom: 22px;
  line-height: 1.6;
}

.form {
  display: flex;
  gap: 12px;
  margin-bottom: 10px;
}

.form input {
  flex: 1;
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 14px 16px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.form input:focus {
  border-color: var(--primary);
  box-shadow: 0 0 0 3px rgba(91, 91, 214, 0.14);
}

.add-button {
  border: none;
  background: var(--primary);
  color: #fff;
  border-radius: 14px;
  padding: 14px 18px;
  font-weight: 700;
  cursor: pointer;
  white-space: nowrap;
  transition: background 0.2s ease, transform 0.2s ease;
}

.add-button:hover {
  background: var(--primary-dark);
  transform: translateY(-1px);
}

.error-message {
  min-height: 22px;
  font-size: 0.95rem;
  color: var(--danger);
  margin-bottom: 12px;
}

.shopping-list {
  list-style: none;
  display: grid;
  gap: 12px;
  margin-top: 6px;
}

.shopping-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 14px;
  padding: 14px 16px;
  border: 1px solid var(--border);
  border-radius: 16px;
  transition: background 0.2s ease, transform 0.2s ease, opacity 0.2s ease;
}

.shopping-item:hover {
  background: #fafafa;
}

.item-check {
  display: flex;
  align-items: center;
  gap: 12px;
  flex: 1;
  cursor: pointer;
}

.item-check input {
  width: 18px;
  height: 18px;
  accent-color: var(--primary);
  cursor: pointer;
}

.item-text {
  font-size: 1rem;
  transition: all 0.2s ease;
}

.shopping-item.completed .item-text {
  text-decoration: line-through;
  opacity: 0.55;
}

.shopping-item.completed {
  opacity: 0.9;
}

.remove-button {
  border: none;
  background: transparent;
  cursor: pointer;
  font-size: 1.1rem;
  padding: 8px;
  border-radius: 10px;
  transition: background 0.2s ease, transform 0.2s ease;
}

.remove-button:hover {
  background: rgba(229, 72, 77, 0.12);
  transform: scale(1.05);
}

.toast {
  position: fixed;
  left: 50%;
  bottom: 20px;
  transform: translateX(-50%);
  background: #111827;
  color: white;
  padding: 14px 18px;
  border-radius: 14px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s ease, transform 0.25s ease;
  font-size: 0.95rem;
}

.toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(-4px);
}

@media (max-width: 600px) {
  .app {
    padding: 16px;
  }

  .card {
    padding: 20px;
    border-radius: 20px;
  }

  h1 {
    font-size: 1.6rem;
  }

  .form {
    flex-direction: column;
  }

  .add-button {
    width: 100%;
  }

  .shopping-item {
    align-items: flex-start;
  }
}

const form = document.getElementById("item-form");
const input = document.getElementById("item-input");
const list = document.getElementById("shopping-list");
const toast = document.getElementById("toast");
const errorMessage = document.getElementById("error-message");

function showToast(message) {
  toast.textContent = message;
  toast.classList.add("show");

  clearTimeout(showToast.timer);
  showToast.timer = setTimeout(() => {
    toast.classList.remove("show");
  }, 2500);
}

function clearError() {
  errorMessage.textContent = "";
}

function showError(message) {
  errorMessage.textContent = message;
}

function createItem(text) {
  const li = document.createElement("li");
  li.className = "shopping-item";

  li.innerHTML = `
    <label class="item-check">
      <input type="checkbox" />
      <span class="item-text"></span>
    </label>
    <button class="remove-button" aria-label="Remover ${text}">🗑️</button>
  `;

  const itemText = li.querySelector(".item-text");
  const checkbox = li.querySelector("input[type='checkbox']");
  const removeButton = li.querySelector(".remove-button");

  itemText.textContent = text;

  checkbox.addEventListener("change", () => {
    li.classList.toggle("completed", checkbox.checked);
  });

  removeButton.addEventListener("click", () => {
    li.remove();
    showToast(`"${text}" removido da lista.`);
  });

  return li;
}

form.addEventListener("submit", (event) => {
  event.preventDefault();

  const value = input.value.trim();

  if (!value) {
    showError("Digite um item antes de adicionar.");
    return;
  }

  clearError();
  const newItem = createItem(value);
  list.appendChild(newItem);
  input.value = "";
  input.focus();
});

document.querySelectorAll(".shopping-item").forEach((item) => {
  const checkbox = item.querySelector("input[type='checkbox']");
  const removeButton = item.querySelector(".remove-button");
  const text = item.querySelector(".item-text").textContent;

  checkbox.addEventListener("change", () => {
    item.classList.toggle("completed", checkbox.checked);
  });

  removeButton.addEventListener("click", () => {
    item.remove();
    showToast(`"${text}" removido da lista.`);
  });
});

input.addEventListener("input", clearError);
