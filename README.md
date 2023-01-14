<!-- this is a README.md for an api docs repo -->
# API dokumentace

## Základní informace
Všechny zálkadní informace o API jsou uvedeny na [https://docs.valkasvetu.tk/](https://docs.valkasvetu.tk/).
<br>
V tomto repu jsou uvedeny příklady kódu pro práci s API v JavaScriptu.

## Routes

### /v1/auth/login
Tato API cesta se používá k přihlášení uživatele do účtu.

```javascript
const login = async (email, password, two_factor_code) => {
    // two_factor_code pouze když je vyžadován
    const response = await fetch('https://api.valkasvetu.tk/v1/auth/login', {
        method: 'POST',
        headers: {
        'Content-Type': 'application/json'
        },
        body: JSON.stringify({
        email,
        password,
        two_factor_code,
        type: 'WEB', //WEB nebo GAME
        description: 'API login', //Jméno přihlášení
        remember_me: true //Pamatovat si uživatele
        })
    });
    const data = await response.json();
    return data.data;
};

const data = login('test@gmail.com', 'password123!1!1!', undefined)
// { session_id: "pHLuW_eUbtKKYGvekc4nH-Ph8RWRBqH2865VBZjFvN", client_identifier: "4c37af06-26b1-4fd6-bab7-7de6332926a4" }
```
