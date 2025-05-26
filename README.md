# xmrig-proxy - Tari (XTM) Fork

This is a **modified fork** of the official [xmrig/xmrig-proxy](https://github.com/xmrig/xmrig-proxy). It has been adapted with specific changes primarily aimed at mining **Tari (XTM)** using its **RandomX** algorithm, along with other modifications.

---

## Key Changes in This Fork

1.  **Tari (XTM) Support Added:**
    * A specific coin entry for "Tari" (`XTM`) has been added, configured to use the `rx/0` (RandomX) algorithm.
    * This allows `xmrig-proxy` to be used with pools supporting Tari merge-mining via RandomX.

2.  **Wallet Address Validation Disabled:**
    * The code responsible for checking the format and validity of miner wallet addresses upon connection has been bypassed.
    * This allows the use of any string as a wallet address, including Tari addresses which might not pass standard Monero validation checks. **Warning:** This increases the risk of mining with an invalid address – **double-check your configurations to avoid lost funds!**

---

## Disclaimer & Warnings

* **No Official Support:** This is an unofficial fork. Do *not* seek support for issues related to these modifications from the official XMRig developers.
* **Use At Your Own Risk:** These changes might introduce instability or have unforeseen consequences. Test thoroughly before deploying in a critical environment.
* **Wallet Validation Disabled:** Be extremely careful with your wallet address configurations. The proxy will no longer warn you about potentially invalid formats. You are solely responsible for ensuring your payouts go to the correct address.

---

Markdown

# xmrig-proxy - Tari (XTM) / No-Fee / No-Validation Fork

This is a **modified fork** of the official [xmrig/xmrig-proxy](https://github.com/xmrig/xmrig-proxy). It has been adapted with specific changes primarily aimed at mining **Tari (XTM)** using its **RandomX** algorithm, along with other modifications.

**USE THIS SOFTWARE AT YOUR OWN RISK. MODIFICATIONS MAY INTRODUCE BUGS OR UNEXPECTED BEHAVIOR. REMOVING DEVELOPER FEES IMPACTS THE PROJECT'S SUSTAINABILITY – CONSIDER SUPPORTING THE ORIGINAL XMRIG DEVELOPERS.**

---

## Key Changes in This Fork

1.  **Tari (XTM) Support Added:**
    * A specific coin entry for "Tari" (`XTM`) has been added, configured to use the `rx/0` (RandomX) algorithm.
    * This allows `xmrig-proxy` to be used with pools supporting Tari merge-mining via RandomX.

2.  **Developer Donation Fee Removed:**
    * The source code has been modified to set the default and minimum developer donation levels to 0%.
    * This completely disables the proxy's developer fee mechanism.

3.  **Wallet Address Validation Disabled:**
    * The code responsible for checking the format and validity of miner wallet addresses upon connection has been bypassed.
    * This allows the use of any string as a wallet address, including Tari addresses which might not pass standard Monero validation checks. **Warning:** This increases the risk of mining with an invalid address – **double-check your configurations to avoid lost funds!**

---

## Disclaimer & Warnings

* **No Official Support:** This is an unofficial fork. Do *not* seek support for issues related to these modifications from the official XMRig developers.
* **Use At Your Own Risk:** These changes might introduce instability or have unforeseen consequences. Test thoroughly before deploying in a critical environment.
* **Wallet Validation Disabled:** Be extremely careful with your wallet address configurations. The proxy will no longer warn you about potentially invalid formats. You are solely responsible for ensuring your payouts go to the correct address.
* **Support Original Developers:** The removal of dev fees directly affects the developers who create and maintain the core XMrig software. If you find XMrig useful, please consider supporting them through other means.

---

Configuration
Create a config.json file. Here is an example configuration for mining Tari (XTM) with RandomX:

JSON Example

{
    "api": {
        "id": null,
        "worker-id": null
    },
    "http": {
        "enabled": false
    },
    "bind": [
        {
            "host": "0.0.0.0",
            "port": 3333, // Port your miners will connect to
            "tls": false
        }
    ],
    "pools": [
        {
            "algo": "rx/0",
            "coin": "XTM", // Use the added Tari coin tag or depends of the pool leave it null
            "url": "your_tari_pool_address:port", // *** REPLACE WITH YOUR POOL ***
            "user": "YOUR_TARI_WALLET_ADDRESS", // *** REPLACE WITH YOUR WALLET ***
            "pass": "x",
            "keepalive": false, // Set to false if your pool gives "Unknown method" errors
            "tls": false
        }
    ],
    "retries": 5,
    "retry-pause": 5,
    "print-time": 60,
    "daemon": false,
    "log-file": null,
    "verbose": true,
    "donate-level": 2
}

Key Points:

Set "coin": "XTM". or depends of the pool leave it null
Set "algo": "rx/0".
Replace the pool url and user with your details.
Set "keepalive": false if you encounter "Unknown method" errors from your specific pool, as some pools do not support the keepalived command.
Running
Navigate to the build directory (or wherever your executable is) and run:

./xmrig-proxy -c config.json
Your miners should then connect to the IP address of the machine running the proxy on the port you specified in the bind section (e.g., 3333).

License
This fork is released under the same GNU General Public License v3.0 as the original xmrig-proxy.
