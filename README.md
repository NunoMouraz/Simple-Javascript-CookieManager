# SimpleJavascriptCookieManager
```javascript
class Cookie {

    /**
     * Gets a cookie
     * @param key
     * @returns {string}
     */
    static get(key) {
        let value = "; " + document.cookie;
        let parts = value.split("; " + key + "=");
        if (parts.length === 2) return parts.pop().split(";").shift();
    }

    /**
     * Creates a cookie
     * @param key
     * @param value
     * @param expires
     */
    static set(key, value, expires) {
        if (typeof expires === 'undefined') {
            expires = 1000 * 60 * 60 * 24 * 15; // ms * s * m * h * d
        }

        let todayDate = new Date();
        let expirationDate = new Date();
        expirationDate.setTime(todayDate.getTime() + expires);
        document.cookie = key + "=" + value + "; expires=" + expirationDate.toGMTString();
    }

    /**
     * Checks if cookie exists
     * @param key
     * @returns {boolean}
     */
    static exists(key) {
        return document.cookie.indexOf(key + "=") > -1;
    }

    /**
     * Deletes a cookie
     * @param key
     */
    static delete(key) {
        if (this.exists(key) ) {
            document.cookie = key + '=; expires=Thu, 01 Jan 1970 00:00:01 GMT;';
        }
    }
}

// Examples
Cookie.set('language', 'en');
Cookie.delete('language');
if (Cookie.exists('language')) {}
```
