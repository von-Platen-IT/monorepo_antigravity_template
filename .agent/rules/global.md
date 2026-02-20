# GLOBAL ARCHITECTURE & SYSTEM RULES (.NET 9 / Vue 3 Monorepo)

## 1. PROJECT STRUCTURE & SCOPING
Dieses Projekt ist ein striktes Monorepo. Du [MUST] deinen Kontext immer auf den aktuellen Ordner beschränken:
- **`apps/web/`**: Reine Vue 3 Single Page Application. Hier existiert [NEVER] C#-Code.
- **`apps/backend/`**: ASP.NET Core 9 Web API. Hier existiert [NEVER] UI-Code (kein HTML, CSS, JS/TS).

## 2. ANTI-HALLUCINATION: FRAMEWORK BOUNDARIES
- [NEVER] generiere Blazor-Komponenten (`.razor`) oder Razor-Pages (`.cshtml`). Das UI ist zu 100 % in Vue 3 ausgelagert.
- [NEVER] schreibe Node.js/Express-Code im Backend. Das Backend ist exklusiv .NET 9.
- Wenn eine Änderung beide Welten betrifft, [MUST] du zuerst das Backend (API & DB) anpassen, das Projekt kompilieren (um Typen zu generieren) und DANN das Frontend aktualisieren.

## 3. THE BRIDGE (API CONTRACT)
- Frontend und Backend kommunizieren ausschließlich über REST (JSON).
- Das Frontend erfindet [NEVER] eigene DTOs (Data Transfer Objects). Es konsumiert ausschließlich die vom Backend (z.B. via NSwag/Kiota) nach `apps/web/src/types/` generierten TypeScript-Interfaces.
