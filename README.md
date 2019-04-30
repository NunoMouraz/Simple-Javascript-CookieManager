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
     */
    static set(key, value) {
        let expiryDate = new Date();
        expiryDate.setMonth(expiryDate.getMonth() + 1);
        document.cookie = key + "=" + value + "; expires=" + expiryDate.toGMTString();
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
```
