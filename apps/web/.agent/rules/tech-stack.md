# Frontend Tech Stack & Guidelines (Vue 3)

**Scope:** `apps/web/` ONLY. Ignoriere alle Backend-Regeln für apps/backend wenn du hier arbeitest.

## 1. Core Stack
- **Framework:** Vue 3 (Vite).
- **Sprache:** TypeScript (Strict Mode).
- **Styling:** Tailwind CSS.

## 2. Component Architecture
- [MUST] Nutze AUSSCHLIESSLICH die Composition API mit `<script setup lang="ts">`.
- [NEVER] nutze die Options API (`export default { data() ... }`).
- Halte Templates sauber. Komplexe Logik gehört in den `<script setup>` Block oder ausgelagerte Composables.

## 3. State Management & API
- **State:** Nutze `Pinia` für globalen Client-State.
- **API-Calls:** Nutze Axios oder native `fetch` API.
- [MUST] Typisiere alle API-Responses streng. Importiere dafür die vom .NET-Backend generierten TypeScript-Interfaces (z.B. aus `src/types/api/`). Erfinde [NEVER] eigene TypeScript-Typen für Backend-Ressourcen.

## 4. Anti-Hallucination: UI Elements
- Nutze ausschließlich Tailwind CSS für das Styling. Generiere [NEVER] custom CSS-Dateien oder `<style scoped>` Blöcke, es sei denn, es ist für hochspezifische Keyframe-Animationen unumgänglich.
