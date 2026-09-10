# 🕵️ OPERACIÓN BANDIT
## Examen práctico · 1 hora · Todo es local

---

## 📜 Reglas

- `unzip nivel-01.zip` → pide contraseña → crea la carpeta `nivel-01/` con todo adentro. Así con cada zip.
- Cada nivel esconde **3 llaves** en formato `CTF{...}`.
- La contraseña del zip siguiente es la **concatenación** de las llaves del nivel actual, **sin `{}`**.
- Anota TODO. Si no anotas, te toca empezar de vuelta.
- Sin internet. Sin `ssh`. Sin `nc`. Solo comandos locales.

**Arsenal permitido:** `ls`, `cat`, `cd`, `file`, `find`, `grep`, `sort`, `uniq`, `tr`, `base64`, `strings`, `zip`, `unzip`, `mv`, `cp`, `diff`, `head`, `tail`.

> 💡 **Consejo:** algunos archivos son señuelos o bromas para gastarte el tiempo. Solo cuentan las llaves con formato `CTF{...}`.

---

## 🗺️ Mapa

```
nivel-01.zip ─(pass: bandit0)─→ llaves 1a, 1b, 1c
   ↓  (1a+1b+1c)
nivel-02.zip ────────────────→ llaves 2a, 2b, 2c
   ↓
nivel-03.zip ────────────────→ llaves 3a, 3b, 3c
   ↓
nivel-04.zip ────────────────→ llaves 4a, 4b, 4c
   ↓
nivel-05.zip ────────────────→ llaves 5a, 5b, 5c  ·  guarda un lockdown.zip
   ↓
lockdown.zip ─(1a + flag 2 + flag 3)─→ 3 misiones finales
   ↓
              Writeup 📄
```

---

## 🚪 NIVEL 1 — pass: `bandit0` · 3 llaves

Tres llaves en nombres de archivo inconformes: uno empieza con un guión, otro es oculto y otro lleva espacios en el nombre.

> `1a + 1b + 1c` = contraseña de `nivel-02.zip`

---

## 📦 NIVEL 2 · 3 llaves

Tres llaves: entre varios archivos solo uno es texto real, otro esconde texto entre datos binarios, y otro guarda un mensaje codificado.

> `2a + 2b + 2c` = contraseña de `nivel-03.zip`

---

## 📦 NIVEL 3 · 3 llaves

Tres llaves: el archivo que pesa exactamente **42 bytes**, el que contiene la palabra **`password`** y el que no tiene extensión.

> `3a + 3b + 3c` = contraseña de `nivel-04.zip`

---

## 📦 NIVEL 4 · 3 llaves

Tres llaves: una línea que nunca se repite, un texto con las letras mudadas y un mensaje codificado.

> `4a + 4b + 4c` = contraseña de `nivel-05.zip`

---

## 📦 NIVEL 5 · 3 llaves

Tres llaves: texto escondido en un archivo binario, una diferencia entre dos archivos casi iguales y una línea única entre repetidas. Guarda el `lockdown.zip` para el final.

> `5a + 5b + 5c` = tu flag de nivel 5

---

## 🔒 lockdown.zip

**Contraseña:** `flag 1a` + `flag 2 completa` + `flag 3 completa`, sin `{}`.

Ejemplo de cómo se arma en general:
```
(1a sin llaves) + (2a+2b+2c sin llaves) + (3a+3b+3c sin llaves)
```

Dentro: 3 misiones finales. Resuélvelas y apunta los resultados.

---

## 📄 Entregable — `writeup.md`

1. Cada llave de los 5 niveles, en orden, con el comando que la encontró.
2. Las 3 misiones del lockdown, con los comandos usados.
3. Un error que cometiste y cómo lo corregiste.
4. La flag completa del nivel 5 bien concatenada (`5a+5b+5c`).

> 🏆 **Bonus:** +1 sobre la nota al primer writeup completo y correcto.