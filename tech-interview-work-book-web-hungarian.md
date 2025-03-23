# Web Modul Kérdések

# -- Modern JS --

## 1. Mi az ECMAScript? Mi a különbség a JavaScript és az ECMAScript között?

Az **ECMAScript (ES)** = Az a **szabvány**, amin a **JavaScript** alapul.

**Különbség:**

-   📜 **ECMAScript** = szabályok/specifikáció
-   💻 **JavaScript** = nyelv, ami implementálja az ES-t + extra funkciók (például DOM)

🔍 Képzeld el úgy, hogy az **ECMAScript a recept**, a **JavaScript pedig a kész étel**.

---

## 2. Magyarázd el az ES6-ban bevezetett „block scoping” koncepciót. Miben különbözik a függvény-szintű hatókörtől?

**Blokk szintű scope** (`let`, `const`) → `{}` blokkokra korlátozódik  
**Függvény szintű scope** (`var`) → az egész függvényre korlátozódik

| Jellemző           | `var` (Function Scope)               | `let` / `const` (Block Scope)              |
| ------------------ | ------------------------------------ | ------------------------------------------ |
| **Scope**          | Egész függvény                       | Csak `{}` blokkon belül                    |
| **Élettartam**     | Függvény teljes futása alatt         | Blokk végéig                               |
| **Hoisting**       | Igen, `undefined` kezdeti értékkel   | Igen, de a **TDZ**-ben a deklarációig      |
| **Újradeklarálás** | Engedélyezett ugyanabban a scope-ban | ❌ Nem engedélyezett ugyanabban a blokkban |

**Példa:**

```js
if (true) {
    var a = 1; // függvény-scope
    let b = 2; // blokk-scope
}
console.log(a); // ✅ 1
console.log(b); // ❌ ReferenceError
```

---

## 3. Mi az a template literal (ES6)? Hogyan könnyíti meg a szövegkezelést JavaScriptben?

**Template Literals (ES6)** = Karakterláncok **backtick (` `)** jelek között → egyszerűbb string kezelés

### 🔑 Előnyök:

-   💬 **Interpoláció:** `${variable}`

```js
let name = "Jack";
console.log(`Hello, ${name}!`);
```

-   📄 **Többsoros stringek:**

```js
let msg = `Line 1
Line 2`;
```

-   ➕ **Kifejezések:** `${a + b}`
-   🏷️ **Tagged templates:** egyedi szövegfeldolgozás

```js
function tag(strings, val) {
    return `${strings[0]}${val.toUpperCase()}`;
}
tag`Hi, ${"jack"}`; // Hi, JACK
```

---

## 4. Mi az a "destructuring assignment" az ES6-ban? Hogyan egyszerűsíti a változók deklarálását, illetve objektumok és tömbök kezelését?

-   Az ES6 **destructuring assignment** lehetővé teszi tömbök vagy objektumok értékeinek egyszerű és tömör kicsomagolását külön változókba.

#### Példa tömbökkel:

```javascript
const numbers = [1, 2, 3];
const [a, b, c] = numbers;
console.log(a, b, c); // 1 2 3
```

#### Példa objektumokkal:

```javascript
const person = { name: "Jack", age: 25 };
const { name, age } = person;
console.log(name, age); // Jack 25
```

---

## 5. Mi az a "spread operator" az ES6-ban? Hogyan könnyíti meg tömbök és objektumok kezelését?

**Spread Operator (`...`)** = Tömbök vagy objektumok egyedi elemekké bontása

### 📚 Tömbök:

```js
const arr1 = [1, 2, 3];
const arr2 = [...arr1]; // másolat
const merged = [...arr1, 4, 5];
```

### 🧩 Objektumok:

```js
const obj1 = { a: 1 };
const obj2 = { ...obj1, b: 2 }; // egyesítés vagy másolás
```

✅ Hasznos másoláshoz, egyesítéshez és elemek átadásához

---

## 6. Mi az ES6-ban bevezetett "default function parameters"? Mutass példát!

**Default Parameters (ES6)** = **alapértelmezett értékek** beállítása függvény paraméterekhez

```js
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}
greet(); // Hello, Guest
greet("Jack"); // Hello, Jack
```

### 💰 Több paraméter:

```js
function calculatePrice(price, tax = 0.1) {
    return price + price * tax;
}
```

✅ Megelőzi az `undefined` hibákat és egyszerűsíti a kódot

---

## 7. Mik az ES6 modulok? Hogyan segítik a kód szervezését és újrahasználhatóságát?

**ES6 Modules** = JS kód felosztása **újrahasználható, rendezett fájlokba**

🔑 **Jellemzők:**

-   🔒 **Kapszulázás**
-   ♻️ **Újrahasználhatóság**
-   🛠️ **Könnyebb karbantartás**
-   ⚡ **Statikus import/export**

```js
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

---

## 8. Mi a különbség a CommonJS és ES6 modulok között?

| Jellemző         | CommonJS (CJS)                 | ES6 Modules (ESM)   |
| ---------------- | ------------------------------ | ------------------- |
| **Syntax**       | `require()` / `module.exports` | `import` / `export` |
| **Végrehajtás**  | Szinkron                       | Aszinkron           |
| **Tree Shaking** | ❌ Nem                         | ✅ Igen             |
| **Használat**    | Node.js                        | Böngészők & Node.js |

---

## 9. Mik a "higher-order function"-ök JavaScriptben?

**Higher-Order Function (HOF)** = Függvény, ami más függvényt kap paraméterként vagy térít vissza.

```js
function multiplyBy(factor) {
    return (num) => num * factor;
}
const double = multiplyBy(2);
double(5); // 10
```

---

## 10. Mi a célja és működése a JavaScriptben található `map` függvénynek? Hogyan különbözik a `filter` és `reduce` függvényektől?

-   A **`map`** függvény új tömböt hoz létre úgy, hogy egy callback függvényt alkalmaz a meglévő tömb minden elemére.

### **Példa:**

```js
const nums = [1, 2, 3];
const squared = nums.map((n) => n * n); // [1, 4, 9]
```

### **Különbségek:**

-   ✅ **`map`** → Transzformál minden elemet, új tömböt ad vissza.
-   ✅ **`filter`** → Új tömböt ad vissza a feltételnek megfelelő elemekkel.
-   ✅ **`reduce`** → Egy értékké csökkenti a tömböt (pl. összeg, szorzat).

-   🚀 **A `map` remek transzformációkhoz!**

---

## 11. Hogyan használható a `filter` függvény tömbök elemeinek szelektív kiválasztására adott feltétel alapján? Mutass példát a `filter` függvényre, amely új tömböt hoz létre, csak a megadott feltételnek megfelelő elemekkel!

-   A JavaScript **`filter`** függvénye új tömböt hoz létre, amely kizárólag a megadott feltételnek megfelelő elemeket tartalmazza.

### **Példa:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
const evens = numbers.filter((n) => n % 2 === 0); // [2, 4, 6]
```

-   ✅ Csak a feltételnek megfelelő elemeket tartja meg.
-   ✅ Új tömböt ad vissza az eredeti módosítása nélkül.

-   🚀 **Ideális dinamikus adatszűrésre!**

---

## 12. Mi a `reduce` függvény szerepe JavaScriptben? Hogyan használható tömbelemek aggregálására vagy egyetlen értékké való összevonására? Mutass példát a `reduce` használatára, ahol összeget vagy maximális értéket számolsz ki egy tömbből!

-   A JavaScript **`reduce`** függvénye egy tömböt dolgoz fel, és egyetlen értéket ad vissza egy úgynevezett reducer függvény segítségével.

### **1. példa: Összegzés**

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, n) => acc + n, 0); // 10
```

### **2. példa: Maximum érték keresése**

```js
const nums = [5, 12, 8, 21];
const max = nums.reduce((acc, n) => Math.max(acc, n), nums[0]); // 21
```

-   ✅ **Használható összegzéshez, max/min kereséshez, átlag számításához, stb.**
-   🚀 **Erőteljes eszköz adatok aggregálásához!**

---

# -- Fetch --

## 1. Hogyan járulnak hozzá a query string paraméterek egy URL-ben a webalkalmazások funkcionalitásához? Magyarázd el, hogyan használjuk őket tipikusan adatok továbbítására weboldalak vagy API-k között.

A **query string paraméterek** kulcs-érték párok, amelyeket a URL-ben a `?` után adunk hozzá.  
→ **Adatok továbbítására** szolgálnak oldalak vagy API-k között.

### 🔧 Példa:

`example.com/products?category=shoes&page=2`

✅ Lehetővé teszik:

-   🔍 Szűrés, keresés, lapozás
-   🧠 Dinamikus tartalom-megjelenítés
-   📊 Felhasználói aktivitás követése
-   🔄 API adatkezelés (pl. rendezés, szűrés, limitálás)

---

## 2. Mi a JavaScriptben található fetch függvény célja és működése?

A **`fetch()`** egy beépített JavaScript függvény, amely **HTTP kérések** (GET, POST, stb.) küldésére szolgál.

✅ Egy **Promise** objektumot ad vissza → lehetővé teszi az **aszinron API-kommunikációt**

### 📦 Példa:

```js
fetch("https://api.example.com/data")
    .then((res) => res.json())
    .then((data) => console.log(data))
    .catch((err) => console.error("Error:", err));
```

🚀 Modern webes alkalmazásokban adatok lekérésére és küldésére használjuk.

---

## 3. Magyarázd el a fetch függvény szintaxisát és azt, hogyan kezeli az aszinkron műveleteket. Hasonlítsd össze a fetch használatát az async/await szintaxissal, valamint a .then() és .catch() szintaxissal. Mik a főbb különbségek, és milyen előnyei vannak az async/await szintaxisnak?

A **`fetch()`** HTTP-kéréseket hajt végre, és egy **Promise**-t ad vissza.

### 🔗 Alap szintaxis (`.then/.catch`-el):

```js
fetch(url)
    .then((res) => res.json())
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

### ✅ Async/await használata (tisztább):

```js
async function getData() {
    try {
        const res = await fetch(url);
        const data = await res.json();
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}
getData();
```

### 🔍 Főbb különbségek:

-   `.then()` → **Promise láncolás**, nehezebb olvashatóság beágyazva
-   `async/await` → **Szinkron kódhoz hasonló**, könnyebben olvasható és hibakereshető

🚀 **Az async/await tisztább, jobb kódszerkezetet eredményez.**

---

## 4. Mi az aszinkronitás JavaScriptben? Sorolj fel néhány tipikus példát, amikor aszinkronitásra van szükség.

Az **aszinkronitás** lehetővé teszi, hogy a JavaScriptben feladatok hajtódjanak végre a főszál **blokkolása nélkül**, lehetővé téve a nem-blokkoló műveleteket.

### **Tipikus példák:**

✅ **API adatok lekérése** (`fetch`, `Axios`).  
✅ **Felhasználói interakciók kezelése** (`setTimeout`, `setInterval`).  
✅ **Fájlok írása/olvasása** (Node.js `fs` modul).  
✅ **Adatbázis-lekérdezések** (MongoDB, Firebase).  
✅ **WebSocketek és valós idejű frissítések** (chat alkalmazások, értesítések).

🚀 **Biztosítja a gördülékeny működést az UI lefagyása nélkül.**

---

## 5. Hogyan dolgozható fel a fetch kérésekre kapott válasz?

A `fetch()` egy **Promise**-t ad vissza, amely egy `Response` objektummá oldódik fel. A válasz feldolgozására használhatjuk a `.json()`, `.text()`, vagy `.blob()` metódusokat.

### Példa: JSON válasz feldolgozása

```javascript
fetch("https://api.example.com/data")
    .then((response) => response.json()) // JSON-ná alakítás
    .then((data) => console.log("Data:", data)) // Adat kezelése
    .catch((error) => console.error("Error:", error)); // Hiba kezelése
```

### Egyéb válaszkezelő metódusok:

-   **`response.text()`** → Egyszerű szöveges válaszokhoz
-   **`response.blob()`** → Képekhez vagy fájlokhoz

---

## 6. Hogyan kezeli a fetch függvény a hibákat és HTTP státuszokat? Adj példát sikeres és hibás válaszok kezelésére.

A JavaScript `fetch()` **nem dob hibát HTTP hibakódokra** (pl. 404, 500), csak **hálózati problémákra**. Manuálisan kell ellenőrizni a `response.ok` és `response.status` értékeket.

### Példa: Siker és hiba kezelése

```javascript
fetch("https://api.example.com/data")
    .then((response) => {
        if (!response.ok) {
            throw new Error(`HTTP Error! Status: ${response.status}`);
        }
        return response.json();
    })
    .then((data) => console.log("Success:", data))
    .catch((error) => console.error("Error:", error.message));
```

---

## 7. Egy URL részeinek magyarázata

### Példa

https://www.example.com:8080/path/page.html?search=query#section

### Fő komponensek:

-   **Protokoll** → `https://` → Kommunikációs mód (pl. HTTP, HTTPS)
-   **Domain** → `www.example.com` → Weboldal címe
-   **Port (Opcionális)** → `:8080` → Kapcsolódási portot határoz meg (alapértelmezett: HTTP - 80, HTTPS - 443)
-   **Útvonal (Path)** → `/path/page.html` → Konkrét erőforrás a szerveren
-   **Query String** → `?search=query` → Kulcs-érték párok adatátvitelhez
-   **Fragment** → `#section` → Ugrás az oldal adott részére

🔹 **Az URL-ek segítenek a webes erőforrások megtalálásában és elérésében.** 🚀

---

# -- Serve --

## 1. Magyarázd el a kliens-szerver kommunikáció koncepcióját webfejlesztési kontextusban! Hogyan áramlik az információ a kliens és a szerver között egy tipikus kliens-szerver architektúrában?

### Kliens-Szerver Kommunikáció a Webfejlesztésben

A **kliens-szerver architektúrában** a **kliens** (böngésző/app) adatokat kér le a **szervertől**, amely feldolgozza a kérést és válaszol.

### Információáramlás:

1. **A kliens kérést küld** → HTTP/HTTPS használatával adatokat kér a szervertől.
2. **A szerver feldolgozza a kérést** → Adatokat lekér, feldolgoz, vagy módosít.
3. **A szerver választ küld** → **HTML, JSON, XML vagy fájlokat** ad vissza.
4. **A kliens megjeleníti az adatokat** → Megjeleníti a választ tartalmát.

### Példa:

```javascript
fetch("https://api.example.com/data")
    .then((response) => response.json())
    .then((data) => console.log(data));
```

---

## 2. Mi az HTTP-kérés és válasz szerepe a webfejlesztésben? Magyarázd el az HTTP kérés és válasz szerkezetét!

### 🌐 HTTP Kérések és Válaszok Webfejlesztésben

HTTP = kommunikáció a **kliens (böngésző)** és a **szerver** között.

### 📤 HTTP kérés (klienstől):

-   **Metódus** → `GET`, `POST`, `PUT`, `DELETE`
-   **URL** → Erőforrás helye (`/api/data`)
-   **Fejlécek (Headers)** → Extra információ (pl. `Content-Type`)
-   **Törzs (Body)** → Adatok küldése (`POST`, `PUT` esetén)

**Példa:**

```
GET /api/users HTTP/1.1
Host: example.com
Authorization: Bearer token123
```

### 📥 HTTP válasz (szervertől):

-   **Státusz kód** → `200`, `404`, `500`, stb.
-   **Fejlécek** → Pl. `Content-Type`
-   **Törzs (Body)** → Visszaadott adatok (JSON, HTML, stb.)

**Példa:**

```
HTTP/1.1 200 OK
Content-Type: application/json

{"id": 1, "name": "Alice"}
```

---

## 3. Magyarázd el a fő különbségeket a CommonJS `require` és az ECMAScript (ES modul) `import` szintaxis között! Hogyan kezelik ezek a megközelítések a JavaScript modulfüggőségeket és exportálásokat?

### Főbb különbségek:

| Tulajdonság      | CommonJS (`require`)           | ES Modulok (`import`)                    |
| ---------------- | ------------------------------ | ---------------------------------------- |
| **Szintaxis**    | `require()` / `module.exports` | `import` / `export`                      |
| **Végrehajtás**  | **Szinkron** (futás közben)    | **Aszinkron** (fordítási időben)         |
| **Környezet**    | Node.js                        | Böngészők és Node.js                     |
| **Tree Shaking** | ❌ Nem                         | ✅ Igen (eltávolítja a felesleges kódot) |

### Példa

**CommonJS:**

```javascript
const math = require("./math.js");
console.log(math.add(5, 3));
```

**ES Modulok:**

```javascript
import { add } from "./math.js";
console.log(add(5, 3));
```

---

## 4. Mik az ES modul szintaxis (`import`) előnyei a CommonJS `require` szintaxisához képest?

✅ **Aszinkron betöltés** → ES modulok **fordítási időben** betöltődnek, növelve a teljesítményt.  
✅ **Tree Shaking támogatás** → Eltávolítja a nem használt kódot, kisebb lesz a csomagméret.  
✅ **Jobb kompatibilitás** → Működik böngészőkben és Node.js-ben is.  
✅ **Tisztább szintaxis** → Könnyebben olvasható és rendezettebb.

---

## 5. Mi az Express.js, és hogyan egyszerűsíti le a Node.js webalkalmazás fejlesztést? Magyarázd el az Express.js főbb jellemzőit és előnyeit!

**Express.js** = Gyors, minimális web keretrendszer **Node.js**-hez.

### 🚀 Fő jellemzők:

-   🔀 **Routing** → HTTP metódusok kezelése (`GET`, `POST`, stb.)
-   ⚙️ **Middleware** → Kérések feldolgozása (autentikáció, naplózás)
-   📁 **Statikus fájlok** → CSS, képek kiszolgálása
-   🖋️ **Template motorok** → EJS, Pug dinamikus oldalakhoz
-   🔗 **REST API támogatás** → Egyszerű JSON alapú API-k
-   🔌 **Bővíthetőség** → Külső middleware/pluginok hozzáadása

✅ Egyszerűbbé, gyorsabbá és skálázhatóvá teszi a backend fejlesztést.

---

## 6. Hogyan kezelhetők statikus fájlok (pl. CSS, képek) Express.js-ben? Hogyan konfigurálható Express.js statikus eszközök kiszolgálására?

Express.js-ben a statikus fájlokat (`express.static`) middleware-rel kezelhetjük. Példa konfiguráció:

```js
app.use(express.static("public"));
```

Ezután a fájlok közvetlenül elérhetők az URL-ekkel (pl. `/images/logo.png`). Virtuális útvonalat is megadhatunk:

```js
app.use("/static", express.static("public"));
```

-   Így a fájlok `/static/images/logo.png` formában érhetők el.

---

## 7. Hogyan kezeli az Express.js az HTTP kérés/válasz ciklusokat? Magyarázd el a kérések fogadásának és a válaszadásnak a folyamatát az Express.js middleware-ek és útvonalkezelők (route handlers) használatával!

### Express.js Kérés/Válasz Ciklus

📥 Amikor egy kérés érkezik:

1. 🔄 **Middleware-ek** futnak sorban → módosítják a kérést, kezelik például az autentikációt, naplózást stb.
2. 🎯 **Útvonalkezelők (Route Handlers)** → Megfelelő HTTP metódus és URL párosítás (például `GET /users`), feldolgozzák a kérést
3. 📤 **Válasz küldése** → Lezárja a ciklust
4. ❌ Ha nincs egyező útvonal → **404-es hiba**
5. ⚠️ Hibák → Speciális **hibakezelő middleware-ek** által kezelve

---

# -- Űrlapok (Forms) --

## 1. Hogyan működik a routing Express.js-ben? Magyarázd el, hogyan definiálhatunk útvonalakat, és hogyan kezelhetünk különböző HTTP metódusokat (GET, POST, stb.) egy Express.js alkalmazásban!

Az Express.js **útvonalak (routes)** határozzák meg, hogyan kezeli a szerver az **HTTP kéréseket** (GET, POST, stb.).

### Útvonalak definiálása:

```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => res.send("Hello, GET!"));
app.post("/data", (req, res) => res.send("POST kérés érkezett"));

app.listen(3000, () => console.log("Szerver fut a 3000-es porton"));
```

✅ **`app.get()`** → GET kérések kezelése  
✅ **`app.post()`** → POST kérések kezelése  
✅ **További metódusok:** `PUT`, `DELETE`, `PATCH`

---

## 2. Milyen módszereket biztosít az Express.js klienseknek való válaszadásra? Magyarázd el a különbséget az Express.js-ben található res.send() és res.json() között!

Az Express több módszert biztosít a válaszadásra:

✅ **`res.send()`** → Szöveg, HTML vagy JSON küldése (automatikusan felismeri a típust)  
✅ **`res.json()`** → JSON válasz küldése (`Content-Type: application/json`-t állít be)  
✅ **`res.redirect()`** → Átirányítás másik URL-re  
✅ **`res.status()`** → HTTP státusz kód beállítása  
✅ **`res.end()`** → Válasz lezárása adat nélkül

### Példa:

```javascript
app.get("/text", (req, res) => res.send("Hello!"));
app.get("/json", (req, res) => res.json({ message: "Hello!" }));
```

---

## 3. Magyarázd el, mit csinál az express.json() middleware!

✅ Az **`express.json()`** egy beépített middleware Express.js-ben, amely **feldolgozza a beérkező JSON adatokat** és elérhetővé teszi őket a `req.body` objektumban.  
✅ Szükséges `POST`, `PUT`, `PATCH` kérésekhez JSON payload kezeléséhez.

### Példa:

```javascript
const express = require("express");
const app = express();

app.use(express.json()); // JSON feldolgozás engedélyezése

app.post("/data", (req, res) => {
    console.log(req.body); // JSON adat elérése
    res.send("JSON megérkezett");
});
```

---

## 4. Mi a next() függvény szerepe az Express.js middleware-ekben? Hogyan használhatod a vezérlés átadására a következő middleware-nek vagy a middleware folyamat lezárására?

✅ A **`next()`** függvény továbbítja a vezérlést a middleware-ek láncában a **következő middleware-nek**.  
✅ Ha nem hívod meg, a kérés **beragad**, válasz nélkül marad.  
✅ Használható **naplózáshoz, autentikációhoz, hibakezeléshez** stb.

### Példa:

```javascript
app.use((req, res, next) => {
    console.log("Middleware végrehajtva");
    next(); // Vezérlés továbbítása a következő middleware-hez vagy útvonalhoz
});

app.get("/", (req, res) => res.send("Hello, World!"));
```

---

## 5. Mi az Express.js-ben az útvonalparaméterek (route parameters) koncepciója? Hogyan nyerhetsz ki dinamikus értékeket az URL útvonalából, és hogyan érhetők el ezek az értékek az útvonalkezelőkben?

✅ Az **útvonalparaméterek** lehetővé teszik **dinamikus értékek** kinyerését az URL-ből.  
✅ A paramétereket a `:` jellel jelöljük az útvonalban.  
✅ Elérésük a `req.params` segítségével történik.

### Példa:

```javascript
app.get("/user/:id", (req, res) => {
    res.send(`Felhasználó azonosítója: ${req.params.id}`);
});
```

### Példa kérés:

```http
GET /user/123
```

### Példa válasz:

```
Felhasználó azonosítója: 123
```

---

## 6. Sorolj fel néhány tipikus HTTP válaszkódot, és magyarázd el jelentésüket!

✅ **Gyakori HTTP státusz kódok**

-   **200 OK** → A kérés sikeres
-   **201 Created** → Erőforrás sikeresen létrejött
-   **400 Bad Request** → Hibás klienskérés
-   **401 Unauthorized** → Hitelesítés szükséges
-   **403 Forbidden** → Hozzáférés megtagadva
-   **404 Not Found** → Erőforrás nem található
-   **500 Internal Server Error** → Szerveroldali hiba

🚀 **A HTTP státuszkódok jelzik a kérés eredményét!**

---

## 7. Sorolj fel néhány tipikus HTTP kérés/válasz fejlécet (headers), és magyarázd el jelentésüket!

### 🔹 **Kérés fejlécek:**

✅ **`Content-Type`** → Meghatározza a kérés adattípusát (például `application/json`)  
✅ **`Authorization`** → Hitelesítési adatok küldése (például `Bearer token`)  
✅ **`Accept`** → Meghatározza, milyen válaszformátumot vár a kliens

### 🔹 **Válasz fejlécek:**

✅ **`Content-Type`** → Meghatározza a válasz adattípusát (például `application/json`)  
✅ **`Cache-Control`** → Gyorsítótárazási viselkedést szabályozza  
✅ **`Set-Cookie`** → Sütiket (cookies) küld a kliensnek

🚀 **A fejlécek metaadatokat biztosítanak a HTTP kommunikációhoz!**

---

## 8. Milyen gyakori HTTP metódusok vannak webfejlesztésben, és milyen célra használjuk őket?

✅ **GET** → Adatok lekérése a szerverről  
✅ **POST** → Adatok küldése a szerverre (új erőforrás létrehozása)  
✅ **PUT** → Erőforrás teljes frissítése/cseréje  
✅ **PATCH** → Erőforrás részleges frissítése  
✅ **DELETE** → Erőforrás eltávolítása

🚀 **Az HTTP metódusok határozzák meg a webes kommunikáció műveleteit!**

---

## 9. Miben különbözik a GET metódus a POST metódustól? Magyarázd el, mikor melyiket célszerű használni! Melyik metódus küld adatokat a kérés törzsében, és melyik a URL-ben küld adatokat?

✅ **GET** → Adatok lekérése, paramétereket **URL-ben (query stringben)** küldi  
✅ **POST** → Adatok küldése, **kérés törzsében** küldi

### Fő különbségek:

| Tulajdonság         | GET                               | POST                           |
| ------------------- | --------------------------------- | ------------------------------ |
| **Cél**             | Adatlekérés                       | Adatküldés/létrehozás          |
| **Adat helye**      | URL (query paraméterek)           | Kérés törzse                   |
| **Biztonság**       | Kevésbé biztonságos (látható URL) | Biztonságosabb (rejtett törzs) |
| **Gyorsítótárazás** | Gyorsítótárazható                 | Nem gyorsítótárazható          |

🚀 **GET adatok olvasásához, POST adatok küldéséhez/módosításához használatos!**

---

## 10. Mire használjuk a PATCH metódust HTTP-ben? Miben különbözik a PUT metódustól, és mikor célszerű erőforrás frissítésére használni?

✅ **PATCH** → Részlegesen frissíti az erőforrást  
✅ **PUT** → Teljesen lecseréli az erőforrást

### Fő különbségek:

| Tulajdonság      | PATCH                       | PUT                      |
| ---------------- | --------------------------- | ------------------------ |
| **Cél**          | Specifikus mezők frissítése | Teljes erőforrás cseréje |
| **Küldött adat** | Csak módosított mezők       | Teljes erőforrás adatai  |
| **Használat**    | Kis módosítások             | Teljes frissítések       |

🚀 **PATCH részleges frissítéshez, PUT teljes lecseréléshez használatos!**

---

## 11. Hogyan használhatjuk a DELETE metódust egy erőforrás eltávolítására a szerverről? Magyarázd el működését és a törlés során figyelembe veendő szempontokat!

✅ **DELETE** → Eltávolít egy erőforrást a szerverről.

### Működése:

1. A kliens `DELETE` kérést küld a szervernek.
2. A szerver feldolgozza és eltávolítja a megadott erőforrást.
3. A szerver válaszol **200 OK**, **204 No Content**, vagy **404 Not Found** státuszokkal.

### Fontos szempontok:

-   **Visszafordíthatatlan** → Ellenőrizd a megerősítést törlés előtt.
-   **Hitelesítés szükséges** → Védd érzékeny adataidat azonosítással.

---

## 12. Hogyan kezeljük az űrlapok beküldését JavaScript segítségével? Magyarázd el az űrlapadatok begyűjtésének folyamatát és az alapértelmezett űrlapbeküldési viselkedés megakadályozását!

✅ **Űrlapadatok begyűjtése** → Használj `document.querySelector()`-t az űrlapelemek elérésére.  
✅ **Alapértelmezett beküldés megakadályozása** → Használj `event.preventDefault()`-et.  
✅ **Adatfeldolgozás** → Olvasd be az értékeket és küldd el `fetch()` vagy `XMLHttpRequest` segítségével.

### Példa:

```javascript
document.querySelector("form").addEventListener("submit", function (event) {
    event.preventDefault(); // Oldal újratöltésének megakadályozása
    const formData = new FormData(event.target);
    console.log(Object.fromEntries(formData)); // Űrlapadatok kiíratása
});
```

---

## 13. Sorold fel a HTML-ben egy űrlap definiálásához szükséges kötelező elemeket!

✅ **`<form>`** → Űrlap konténer  
✅ **`action`** → URL, ahová az adatok kerülnek  
✅ **`method`** → HTTP metódus (`GET` vagy `POST`)  
✅ **`<input>`** → Felhasználói adatmezők  
✅ **`name`** → Mezők azonosítója  
✅ **`<label>`** → Mező leírása  
✅ **`<button type="submit">`** → Űrlap beküldése

### Példa:

```html
<form action="/submit" method="POST">
    <label for="name">Név:</label>
    <input type="text" id="name" name="name" required />
    <button type="submit">Küldés</button>
</form>
```

---

## 14. Mi a HTML űrlapokban található `required` attribútum célja? Hogyan kényszeríti ki a kötelező mezők kitöltését, és akadályozza meg az űrlap beküldését, ha a szükséges információ hiányzik?

✅ **Kötelező mező kitöltése** → Megakadályozza az űrlap beküldését, ha a mező üres.  
✅ **Használható `<input>`, `<textarea>`, `<select>` elemekkel** → Kötelezővé teszi az adatok megadását.  
✅ **Beépített validáció** → JavaScript nélkül is hibaüzenetet jelenít meg.

### Példa:

```html
<form>
    <input type="text" name="username" required />
    <button type="submit">Küldés</button>
</form>
```

---

## 15. Sorold fel a HTML űrlapok különböző típusú input mezőit, és magyarázd el azok különbségeit és felhasználásukat!

✅ **`text`** → Egysoros szöveges bevitel (pl. név, felhasználónév)  
✅ **`number`** → Számok bevitele (pl. életkor, mennyiség)  
✅ **`email`** → Email formátum ellenőrzése (`pelda@mail.com`)  
✅ **`checkbox`** → Többszörös választás (pl. érdeklődési körök)  
✅ **`radio`** → Csak **egy választás** egy csoportból (pl. nem)

### Példa:

```html
<form>
    <input type="text" placeholder="Név" />
    <input type="number" placeholder="Életkor" />
    <input type="email" placeholder="Email" />
    <input type="checkbox" /> Feliratkozás
    <input type="radio" name="gender" value="male" /> Férfi
    <input type="radio" name="gender" value="female" /> Nő
</form>
```

---

## 16. Mi a `name` attribútum szerepe az űrlapbeküldés során?

-   A form-elemek `name` attribútuma azonosítja az input mezőket, és elengedhetetlen az űrlap beküldéséhez. Az űrlap beküldésekor a böngésző kulcs-érték párokat küld, ahol a kulcs a `name` attribútum értéke, az érték pedig a beírt adat.

### Példa:

```html
<input type="text" name="username" value="KissJozsef" />
```

-   Beküldve: **`username=KissJozsef`** formátumban.

-   A `name` nélkül az adott mező adata nem kerül beküldésre, ezért elengedhetetlen a szerveroldali feldolgozás során.

---

## 17. Hogyan kapcsolhatjuk össze a `<label>` címkét egy form-elemmel?

### 🔗 `<label>` összekapcsolása form-elemekkel

1️⃣ **`for` attribútum használata (ajánlott):**

```html
<label for="username">Felhasználónév:</label>
<input type="text" id="username" name="username" />
```

✔ A label kattintásával a mező aktívvá válik

2️⃣ **Input elem címkébe csomagolása:**

```html
<label>Felhasználónév: <input type="text" name="username" /></label>
```

✔ Működik `id` nélkül is, a mező aktívvá válik

✅ **A `for` attribútum jobb akadálymentességet biztosít**

---

## 18. Hogyan módosíthatjuk dinamikusan a form-elemeket JavaScript segítségével? Magyarázd el, hogyan adhatunk hozzá vagy távolíthatunk el dinamikusan mezőket felhasználói interakció vagy feltételek alapján!

### ✨ Dinamikus űrlapkezelés JavaScript-tel

📥 **Új input mező hozzáadása:**

```js
const form = document.getElementById("form");
const newInput = document.createElement("input");
newInput.type = "text";
newInput.name = "dynamicField";
form.appendChild(newInput);
```

❌ **Input mező eltávolítása:**

```js
const inputToRemove = document.getElementById("inputId");
inputToRemove.remove();
```

⚡ **Mező hozzáadása gombnyomásra (Event Listener):**

```js
document.getElementById("addBtn").addEventListener("click", () => {
    const input = document.createElement("input");
    input.type = "text";
    document.getElementById("form").appendChild(input);
});
```

✅ Használj **eseményfigyelőket** mezők dinamikus kezeléséhez.

---

## 19. Hogyan alakíthatjuk át az űrlapadatokat szerver számára könnyen továbbítható vagy feldolgozható formátumra?

### 📤 Űrlapadatok szerverre való alakítása

1️⃣ **URL-kódolt (alapértelmezett HTML form):**

```js
const formData = new URLSearchParams(new FormData(formElement)).toString();
```

2️⃣ **JSON (API-khoz):**

```js
const formObject = Object.fromEntries(new FormData(formElement).entries());
const jsonData = JSON.stringify(formObject);
```

3️⃣ **FormData (fájlokhoz/multipart adatokhoz):**

```js
const formData = new FormData(formElement);
```

✅ Formátumot mindig a **szerver követelményeihez** igazítsd!

---

# -- React --

## 1. Mi az a React.js és mik a főbb jellemzői?

A **React.js** egy JavaScript könyvtár **felhasználói felületek (UI)** építésére.  
⚛️ **Főbb jellemzők:**

-   🔁 **Komponensek** → Újrahasználható UI egységek
-   ⚡ **Virtuális DOM** → Gyors felhasználói felület frissítés
-   📜 **JSX** → HTML-szerű szintaxis JavaScriptben
-   🔄 **Egyirányú adatáramlás** → Kiszámítható állapotkezelés
-   🛠️ **Deklaratív** → Világos és egyszerű kód

---

## 2. Magyarázd el a virtuális DOM koncepcióját és hogy hogyan járul hozzá a React teljesítményéhez!

A **virtuális DOM** a valódi DOM egy könnyű, virtuális másolata.

⚙️ **Teljesítménynövelés folyamata:**

1. 📝 A változások először a **virtuális DOM-ban** jelennek meg
2. 🔍 A React összehasonlítja az előző verzióval (**diffing**)
3. 🎯 Csak azok a valódi DOM részek frissülnek, amelyek változtak (**hatékony frissítés**)

➡️ Eredmény: **Gyorsabb, gördülékenyebb UI megjelenítés**

---

## 3. Magyarázd el a komponens-alapú architektúrát React.js-ben! Hogyan működnek a komponensek, és hogyan építhetők fel belőlük komplex felhasználói felületek?

A **komponens-alapú architektúra** egy olyan UI építési mód, amely **független, újrafelhasználható részekből** áll.

🔧 **A komponensek működése:**

-   📦 Minden komponens egy kis UI egység (saját logikával, HTML-lel és stílussal)
-   🔄 Képes fogadni **prop-okat** (inputokat) és kezelni **állapotokat** (belső adatokat)

🏗️ **UI összeállítása:**

-   🔲 **Kis komponensek** → nagyobb egységekbe szerveződnek
-   🧩 Mint építőkockák → könnyen létrehozható komplex felhasználói felület

---

## 4. Mi a JSX jelentősége React.js-ben? Magyarázd el, hogyan kombinálja a JSX a HTML-szerű szintaxist JavaScript kóddal, és hogyan kerül átfordításra hagyományos JavaScript kódra a build folyamat során!

A **JSX** egy HTML-szerű szintaxis a **JavaScript-en** belül.

💡 **Miért fontos:**

-   📝 Könnyebben **olvashatóvá és érthetővé** teszi a UI kódját
-   💬 Lehetővé teszi **HTML és JS logika együttes írását**

⚙️ **A háttérben:**

-   🔁 JSX **átfordítása (Babel által)** → hagyományos JavaScript kóddá (`React.createElement`)
-   📦 Segíti a Reactet a **UI struktúrájának hatékony felépítésében**

---

## 5. Mi a prop-ok szerepe Reactben, és hogyan használhatók adatok átadására komponensek között? Magyarázd el a prop-ok koncepcióját, és hogy miként segítik a szülő-gyerek komponensek közötti kommunikációt!

A **prop-ok** a **szülő** komponensből **gyerek** komponensekbe küldött **inputok**.

📦 Használatuk:

-   Adatok vagy függvények küldése gyerek komponensekbe
-   Komponensek dinamikussá és újrahasználhatóvá tétele

🔗 **Szülő → Gyerek kommunikáció:**

```jsx
<ChildComponent title="Hello" />
```

➡️ **ChildComponent ezt kapja:** `props.title = "Hello"`

✅ **Prop-ok csak olvashatók:** a gyerek komponensben nem módosíthatók

---

## 6. Hogyan érhetők el és használhatók a prop-ok React funkcionális komponenseiben? Magyarázd el, hogyan bonthatók ki és használhatók a prop-ok destrukturálással!

📥 **Prop-ok elérése funkcionális komponensben:**

```jsx
function Greeting(props) {
    return <h1>Hello, {props.name}</h1>;
}
```

🔓 **Prop-ok destrukturálása:**

```jsx
function Greeting({ name }) {
    return <h1>Hello, {name}</h1>;
}
```

✅ **Tisztább és könnyebben olvasható**, főleg több prop esetén

---

## 7. Hogyan adhatunk át callback függvényeket prop-ként React-ben? Mutass példát arra, hogyan adhatunk át egy függvényt egy szülő komponensből egy gyerek komponensnek, lehetővé téve ezzel, hogy a gyerek kommunikáljon a szülővel!

🔁 **Callback függvény átadása prop-ként** = lehetővé teszi, hogy a **gyerek komponens akciókat indítson a szülő komponensben**

📦 **Szülő → Gyerek:**

```jsx
function Parent() {
    const handleClick = () => alert("Kattintva!");
    return <Child onClick={handleClick} />;
}
```

👶 **Gyerek használja a függvényt:**

```jsx
function Child({ onClick }) {
    return <button onClick={onClick}>Kattints rám</button>;
}
```

✅ **Lehetővé teszi a szülő-gyerek kommunikációt**

---

## 8. Magyarázd el a prop-ok spreadelésének koncepcióját React-ben! Hogyan használható a spread operátor (`...`) több prop egyszerű és átlátható módon történő átadására szülő komponensből gyerek komponensbe?

A **prop spreadelés** lehetővé teszi több prop egyszerre történő átadását a **spread operátor (`...`) segítségével**, ami tisztább, átláthatóbb kódot eredményez.

✅ **Példa:**

```jsx
const props = { name: "János", age: 30 };
<Profile {...props} />;
```

Ez egyenértékű ezzel:

```jsx
<Profile name="János" age={30} />
```

✅ Hasznos **újrahasználható komponenseknél** és **dinamikus prop-átadásnál**.

---

## 9. Mi a default prop-ok (alapértelmezett prop-ok) koncepciója React-ben (ES6 JS szintaxissal)? Hogyan definiálhatunk alapértelmezett értékeket komponensek prop-jaihoz arra az esetre, ha az adott prop értéke nincs explicit átadva?

A **default prop-ok** olyan alapértelmezett értékek, amelyeket akkor használunk, ha a prop nincs átadva a komponensnek.

✅ **ES6 szintaxis:**
Alapértelmezett értékek közvetlenül a függvény paramétereiben:

```jsx
function Greeting({ name = "Vendég" }) {
    return <h1>Üdv, {name}!</h1>;
}
```

✅ Segít elkerülni az **undefined értékeket**, robusztusabbá és kiszámíthatóbbá teszi a komponenseket.

---

## 10. Magyarázd el az immutabilitás (változatlanság) elvét React prop-jaival és állapotaival kapcsolatban! Miért fontos elkerülni a prop-ok közvetlen módosítását komponenseken belül, és milyen legjobb gyakorlatok segítenek az immutabilitás fenntartásában?

React-ben a **prop-ok és state-ek közvetlenül nem módosíthatók**. Ehelyett mindig **új példányokat** hozunk létre az állapot módosításakor, ezzel megőrizve az **immutabilitást**.

✅ **Miért fontos:**  
Az immutabilitás segít a React-nek változásokat érzékelni, így hatékonyan újra tudja renderelni a komponenseket.

✅ **Legjobb gyakorlatok:**

-   Használj spread operátort (`...`) objektumok és tömbök módosítására
-   Soha ne módosítsd közvetlenül a prop-okat

---

## 11. Hogyan kezeli a React.js az állapotkezelést? Magyarázd el a state koncepcióját és azt, hogy miben különbözik a prop-októl!

A **state** dinamikus, helyi adatokat tárol egy komponensben, amelyek változhatnak a `useState` hook segítségével.  
A **prop-ok** szülőtől gyerekbe átadott, csak olvasható értékek.

✅ **Fő különbség:**

-   **State**: belső, módosítható.
-   **Prop-ok**: külső, csak olvasható.

---

## 12. Mik azok a React hook-ok? Magyarázd el a React.js-ben található hook-ok, például a `useState`, `useEffect` célját és előnyeit!

A **React Hook-ok** olyan függvények, amelyek **állapotkezelést** és **életciklus-kezelést** adnak funkcionális komponensekhez.

### 🔧 Gyakori Hook-ok:

-   **`useState`** → Helyi állapot kezelése
-   **`useEffect`** → Mellékhatások kezelése (pl. adatlekérés, DOM-műveletek)

✅ **Előnyök:**

-   Tisztább, olvashatóbb kód
-   Újrahasználható logika (egyedi hook-ok)
-   Nem szükséges osztály-alapú komponenseket használni
-   Jobb életciklus-kezelés

---

## 13. Magyarázd el a virtuális DOM reconciliation koncepcióját React.js-ben! Hogyan frissíti és rendereli hatékonyan a komponenseket React, minimális DOM manipulációval?

A **virtuális DOM** a valódi DOM könnyű másolata, amelyet a React használ.

🔁 Állapot/prop változáskor:

-   React létrehoz egy **új virtuális DOM-ot**
-   Összehasonlítja az előzővel (**diffing**)
-   Csak a **változott részeket** frissíti a valódi DOM-ban (**reconciliation**)

✅ Gyorsabb frissítések → **Jobb teljesítmény és gördülékenyebb UI**

---

## 14. Hogyan kezelhetünk komplex állapotobjektumokat a `useState` hook segítségével? Magyarázd el az objektumok spreadelését vagy egyesítését az objektum állapot specifikus tulajdonságainak frissítésére!

### 🔄 Komplex állapotok kezelése a `useState`-tel

❌ **Kerüld a közvetlen módosítást** → Mindig hozz létre egy **új objektumhivatkozást**

✅ **Használj objektum spreadelést specifikus tulajdonságok frissítésére:**

```jsx
const [user, setUser] = useState({ name: "Alíz", age: 25 });

setUser({ ...user, age: 26 }); // Csak az életkort frissíti, a nevet megtartja
```

📌 **Mélyen beágyazott állapot esetén** használj több spread operátort, vagy fontold meg a **`useReducer`** használatát.

---

## 15. Miért fontos új tömböt megadni a `useState` hook számára, amikor új elemet adunk egy meglévő tömbhöz?

React-ben az állapotfrissítéseknek **változatlannak (immutable)** kell lenniük, hogy React észlelje a változást és újra renderelje a komponenst. A meglévő tömb közvetlen módosítása (például `push()`-al) nem hoz létre új hivatkozást, ezért React nem mindig érzékeli a változást.

✅ Ehelyett hozz létre **új tömböt** spread operátorral vagy tömbmódszerekkel:

```jsx
setItems([...items, newItem]);
```

---

## 16. Hogyan működik a feltételes renderelés React-ben? Magyarázd el a különböző technikákat, amelyek lehetővé teszik a komponensek vagy tartalom feltételes megjelenítését állapot- vagy prop-értékek alapján! Hogyan használhatjuk ezt komponensek láthatóságának vagy viselkedésének dinamikus szabályozására?

### 🔀 Feltételes renderelés React-ben

Tartalom megjelenítése **feltételek (state/prop)** alapján.

### ✅ Gyakori technikák:

1️⃣ **if/else (JSX-en kívül):**

```jsx
if (isLoggedIn) return <Dashboard />;
else return <Login />;
```

2️⃣ **Ternáris operátor (inline):**

```jsx
{
    isLoggedIn ? <Dashboard /> : <Login />;
}
```

3️⃣ **Logikai ÉS (`&&`):**

```jsx
{
    isAdmin && <AdminPanel />;
}
```

📌 **Használati esetek:**

-   Tartalom megjelenítése/elrejtése
-   Betöltők vagy hibák megjelenítése
-   Nézetek közötti váltás (például belépési oldal és dashboard)

---

## 17. Hogyan hozhatunk létre select input elemet React-ben? Miben különbözik a React select eleme a HTML select tag-jétől? Mutass példát kontrollált és nem kontrollált select elemre, alapértelmezett érték beállításával!

### 🔽 Kontrollált vs Nem kontrollált `<select>` React-ben

#### ✅ **Kontrollált Select (React állapot kezeli az értéket):**

```jsx
const [option, setOption] = useState("apple");

<select value={option} onChange={(e) => setOption(e.target.value)}>
    <option value="apple">Alma</option>
    <option value="banana">Banán</option>
    <option value="orange">Narancs</option>
</select>;
```

#### ❎ **Nem kontrollált Select (DOM kezeli az értéket):**

```jsx
<select defaultValue="banana">
    <option value="apple">Alma</option>
    <option value="banana">Banán</option>
    <option value="orange">Narancs</option>
</select>
```

### 🔑 Fő különbség:

-   **Kontrollált** → `value` + `onChange` = **React által vezérelt**
-   **Nem kontrollált** → `defaultValue`, nincs állapotkövetés (React nem kezeli a frissítéseket)

---

# -- Adatbázis --

## 1. Mi az a MongoDB, és miben különbözik a hagyományos relációs adatbázisoktól? Magyarázd el a MongoDB kulcsfontosságú jellemzőit és előnyeit mint NoSQL adatbázis-megoldás!

### 📦 MongoDB áttekintés

A **MongoDB** egy NoSQL, dokumentum alapú adatbázis, amely **BSON (JSON-szerű)** formátumot használ.

### 🔍 Főbb különbségek az RDBMS-től:

-   📄 **Séma nélküli** → Rugalmas struktúra (nincsenek fix oszlopok)
-   ⚡ **Vízszintes skálázhatóság** → Támogatja a shardingot
-   🔍 **Gazdag lekérdezések és indexelés** → Hatékony adat-hozzáférés
-   🔗 **Nincs Join** → **Beágyazott dokumentumokat** használ

### ✅ Előnyök:

-   ⚡ Gyors olvasás/írás teljesítmény
-   🔄 Rugalmas és jól skálázható (ideális nagy adatmennyiségekhez és valós idejű alkalmazásokhoz)
-   💬 JSON-szerű adatok → Könnyű JavaScript integráció
-   🛡️ Magas rendelkezésre állás **automatikus failover és replikáció** révén

---

## 2. Magyarázd el a kollekciók (collections) és dokumentumok (documents) koncepcióját MongoDB-ben! Hogyan tárolja és szervezi a MongoDB az adatokat?

### 📂 MongoDB: Kollekciók és Dokumentumok

-   **Dokumentum** = JSON-szerű BSON objektum  
    👉 Példa: `{ name: "USA", population: 331000000 }`

-   **Kollekció** = Kapcsolódó dokumentumok csoportja (hasonló a táblákhoz, de **séma nélküli**)

### 📦 Adattárolás és szervezés:

-   Adatok tárolása **rugalmas dokumentumokban**
-   A **kollekciók** hasonló adatokat tartalmaznak fix struktúra nélkül
-   **Index-alapú motor** biztosítja a gyors lekérést
-   Támogatja a **beágyazott** (nested) és **hivatkozott** (referenced) dokumentum-kapcsolatokat

---

## 3. Mi az a Mongoose.js, és hogyan egyszerűsíti a MongoDB-vel való munkát Node.js környezetben? Magyarázd el a Mongoose.js kulcsfontosságú jellemzőit és előnyeit!

### 🧠 Mongoose.js áttekintés

A **Mongoose** egy ODM (Object Data Modeling) könyvtár **MongoDB + Node.js** számára.

### 🔑 Kulcsfontosságú jellemzők:

-   📐 **Séma definíciók** → Strukturált adatmodellek
-   ✅ **Validáció** → Adatok ellenőrzése mentés előtt
-   🔄 **Middleware (Hooks)** → Pre/post folyamatok kezelése (például jelszó hashelés)
-   🔍 **Lekérdezés építő** → Egyszerű CRUD műveletek
-   🧮 **Virtuális mezők és metódusok** → Számított mezők és egyéni függvények

### ✅ Előnyök:

-   Tisztább, fenntarthatóbb kód
-   Biztosítja az adatok következetességét
-   Tökéletesen működik **async/await**-tel
-   Támogatja a **kapcsolatokat és adat populációt**

---

## 4. Hogyan definiálunk és hozunk létre sémákat (schemas) Mongoose.js-ben? Magyarázd el, hogy a sémák hogyan határozzák meg a MongoDB kollekciók dokumentumainak struktúráját és validációs szabályait!

✅ Mongoose-ban a **sémák határozzák meg a dokumentumok struktúráját és validációs szabályait**.

```js
const mongoose = require("mongoose");
const Schema = mongoose.Schema;

const UserSchema = new Schema({
    name: { type: String, required: true },
    age: { type: Number, min: 0 },
    email: { type: String, unique: true },
});
```

✅ Ezután létrehozunk egy **modellt** a sémából:

```js
const User = mongoose.model("User", UserSchema);
```

A sémák segítenek kikényszeríteni az **adat-típusokat, korlátozásokat és validációs szabályokat**.

---

## 5. Magyarázd el a különböző adatmodellezési technikákat Mongoose.js-ben! Hogyan definiálhatunk kapcsolatokat MongoDB kollekciók között (egy-egy, egy-sok, sok-sok kapcsolat)?

✅ A Mongoose különböző **adatmodellezési technikákat** támogat kapcsolatok definiálására:

-   **Egy-egy kapcsolat:**

```js
const ProfileSchema = new Schema({
    user: { type: mongoose.Schema.Types.ObjectId, ref: "User" },
});
```

-   **Egy-sok kapcsolat:**

```js
const BlogSchema = new Schema({
    comments: [{ type: mongoose.Schema.Types.ObjectId, ref: "Comment" }],
});
```

-   **Sok-sok kapcsolat:**

```js
const StudentSchema = new Schema({
    courses: [{ type: mongoose.Schema.Types.ObjectId, ref: "Course" }],
});

const CourseSchema = new Schema({
    students: [{ type: mongoose.Schema.Types.ObjectId, ref: "Student" }],
});
```

✅ Ezeket a kapcsolatokat a `.populate()` segítségével kezelhetjük.

---

## 6. Milyen lehetőségeket biztosít a Mongoose.js az adatok lekérdezésére és manipulálására? Magyarázd el, hogyan végezhetünk CRUD műveleteket (létrehozás, olvasás, frissítés, törlés) Mongoose.js metódusokkal és lekérdezésekkel!

✅ A Mongoose beépített metódusokat kínál **CRUD műveletek** végrehajtására:

-   **Létrehozás (Create):** `Model.create()` vagy `new Model().save()`

```js
User.create({ name: "Alíz", age: 25 });
```

-   **Olvasás (Read):** `Model.find()`, `Model.findById()`, `Model.findOne()`

```js
User.find({ age: 25 });
```

-   **Frissítés (Update):** `Model.updateOne()`, `Model.findByIdAndUpdate()`

```js
User.updateOne({ name: "Alíz" }, { age: 26 });
```

-   **Törlés (Delete):** `Model.deleteOne()`, `Model.findByIdAndDelete()`

```js
User.deleteOne({ name: "Alíz" });
```

✅ Ezek a metódusok lehetővé teszik a MongoDB-ben történő hatékony lekérdezést és adatkezelést.

---

## 7. Hogyan csatlakozhatunk egy MongoDB adatbázishoz Mongoose.js segítségével? Magyarázd el, hogyan konfigurálhatunk és hozhatunk létre kapcsolatot egy MongoDB szerverrel Node.js alkalmazásban a Mongoose.js használatával!

A **Mongoose.js** egy ODM (Object Data Modeling) könyvtár MongoDB-hez és Node.js-hez.

✅ **Alapvető kapcsolat létrehozása:**

```js
const mongoose = require("mongoose");

mongoose
    .connect("mongodb://localhost:27017/mydb", {
        useNewUrlParser: true,
        useUnifiedTopology: true,
    })
    .then(() => console.log("Csatlakozva a MongoDB-hez"))
    .catch((err) => console.error("Csatlakozási hiba:", err));
```

✅ A Mongoose leegyszerűsíti a sémák létrehozását, adatvalidációt és lekérdezéseket MongoDB-ben.

---

# -- MERN --

## 1. Mi a React Router koncepciója? Hogyan teszi lehetővé a kliensoldali útválasztást React.js alkalmazásokban, és hogyan segíti több oldalszerű élmény létrehozását?

-   ### **React Router**
    A React Router egy React **útválasztó könyvtár**, amely lehetővé teszi a **kliensoldali navigációt**, ezzel több oldalszerű élményt biztosít oldal-újratöltés nélkül.

### **Működése:**

✅ Használja a **History API**-t a dinamikus URL-frissítéshez.  
✅ Az **útvonalak (Routes)** URL-eket komponensekhez rendelnek, útvonal alapján renderelve azokat.  
✅ Támogat **beágyazott útvonalakat**, átirányításokat és dinamikus paramétereket.

### **Előnyök:**

✔ **Gyors navigáció** – Nincs teljes oldal-újratöltés.  
✔ **Single Page Application (SPA)** – Többoldalas érzet.  
✔ **Deklaratív útválasztás** – Könnyen kezelhető útvonal-komponensek.

---

## 2. Mi a szerveroldali útválasztás koncepciója Express.js-ben? Hogyan kezeli az Express a beérkező kéréseket, és hogyan irányítja azokat a megfelelő API végpontokhoz vagy route-kezelőkhöz?

-   ### **Szerveroldali útválasztás Express.js-ben**
    Az Express.js **szerveroldali útválasztást** végez, a **beérkező kéréseket** (URL-eket) konkrét **route-kezelőkhöz** rendeli.

### **Működése:**

✅ Használja az `app.METHOD(PATH, HANDLER)` módszert (pl. `app.get('/users', handler)`).  
✅ **Middleware-ek és kontrollerek** dolgozzák fel a kéréseket válaszadás előtt.  
✅ Támogat **dinamikus útvonalakat**, query-paramétereket és csoportosítást az `express.Router()` segítségével.

### **Előnyök:**

✔ **Hatékony API kezelés** backend szolgáltatásokhoz.  
✔ **Moduláris és skálázható** struktúra routerekkel.  
✔ **Middleware támogatás** autentikációhoz, naplózáshoz, stb.

🚀 **Alapvető a MERN backend fejlesztéshez!**

---

## 3. Mi az a MERN stack? Magyarázd el a MERN stack egyes komponenseit, és azok szerepét webalkalmazások fejlesztésében!

-   ### **MERN Stack**
    A MERN egy **JavaScript-alapú** technológiai stack teljes értékű webes alkalmazások készítésére.

### **Komponensek és szerepük:**

✅ **MongoDB** – NoSQL adatbázis adatok tárolásához.  
✅ **Express.js** – Backend keretrendszer API kérések kezeléséhez.  
✅ **React.js** – Frontend könyvtár felhasználói felületekhez.  
✅ **Node.js** – JavaScript futtatókörnyezet szerveroldalon.

💡 **A MERN stack lehetővé teszi a teljes stack JavaScript fejlesztést, gyors és skálázható alkalmazások építését!** 🚀

---

## 4. Hogyan működik a proxy React fejlesztés során? Hogyan lehet a webpack dev szervert proxyzásra beállítani a backend felé? Milyen URL-eket kell használnod a fetch hívások során JavaScriptben, ha proxy-t használsz?

-   ### **Proxy használata React fejlesztés során**
    A **proxy** segít áthidalni a CORS problémákat azáltal, hogy a frontend kéréseket a backend felé továbbítja fejlesztési környezetben.

### **Proxy beállítása React-ben:**

1. Add hozzá a `package.json` fájlhoz:

```json
"proxy": "http://localhost:5000"
```

2. Használj **relatív URL-eket** a `fetch` hívásokban:

```js
fetch("/api/data"); // Proxy-zva backend-re
```

### **Működése:**

✅ Webpack Dev Server **továbbítja** a kéréseket a `localhost:5000`-re.  
✅ Nem kell teljes backend URL-eket használni a `fetch`-ben.  
✅ Egyszerűsíti az API-hívásokat fejlesztés közben. 🚀

---

## 5. Mik a MERN stack használatának előnyei webfejlesztés során? Hogyan járul hozzá a MERN stack egyes komponense a fejlesztési folyamathoz és a modern webalkalmazások építésének általános hatékonyságához?

✅ **MERN Stack** = Teljes értékű JavaScript megoldás webalkalmazásokhoz

-   **MongoDB** → NoSQL adatbázis (rugalmas tárolás)
-   **Express.js** → Backend útválasztás és API kezelés
-   **React.js** → Dinamikus felhasználói felületek
-   **Node.js** → Szerveroldali JavaScript

✅ **Előnyök:**

-   Gyors fejlesztés
-   Újrahasználható komponensek
-   Skálázható architektúra
-   Egyetlen nyelv az egész stack-ben

---

## 6. Hogyan áramlanak az adatok a MERN stack architektúrában? Magyarázd el, hogy a React frontend hogyan kommunikál a Node.js és Express.js backenddel a kliens kérések kezelése és a MongoDB adatbázis adatok kiszolgálása érdekében!

✅ A **MERN stack**-ben az adatok így áramlanak:

➡️ **React (kliens)** → `fetch` → **Express (API)** → **MongoDB (Mongoose-on keresztül)** → Válasz → **React (UI frissítés)**

📦 React kéréseket küld → Express kezeli a logikát → MongoDB tárolja/visszaküldi az adatokat → A válasz visszajut a React-be

✅ Teljes értékű JS stack **frontend + backend + adatbázis** között
