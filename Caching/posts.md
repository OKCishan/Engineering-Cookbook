**Major Cache issues and its solution**

𝐂𝐚𝐜𝐡𝐞 & 𝐢𝐭𝐬 𝐭𝐡𝐫𝐞𝐞 𝐦𝐚𝐢𝐧 𝐩𝐫𝐨𝐛𝐥𝐞𝐦𝐬 & 𝐬𝐨𝐥𝐮𝐭𝐢𝐨𝐧𝐬 <br />
While caching is great, but its careless use can raise 3 main issues👇🏼

𝐈𝐒𝐒𝐔𝐄 1️⃣ : 𝐂𝐚𝐜𝐡𝐞 𝐩𝐞𝐧𝐞𝐭𝐫𝐚𝐭𝐢𝐨𝐧. <br />
The case when the data queried is neither present in database nor in cache. As a result, the request will be directed from cache to database eventually, penetrating the cache layer and defeating the whole purpose of caching. It can be due to some malicious attack. <br />
𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧: <br />
💡 Cache keys with null value. Prefer short TTL (Time to Live) for keys with null value. <br />
💡Use Bloom filters. Basically it can tell whether a key is present in a set or not very quickly. Then if not present, ignore that calls completely, i.e. such calls should neither hit cache nor database. <br />


𝐈𝐒𝐒𝐔𝐄 2️⃣ : 𝐂𝐚𝐜𝐡𝐞 𝐚𝐯𝐚𝐥𝐚𝐧𝐜𝐡𝐞. <br />
If the cache goes down for some reason, the massive query request that was originally blocked by the cache will flock to the database like a mad dog. At this point, if the database can’t withstand this huge pressure, it will collapse. <br />
𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧: <br />
💡 Ensure high availability of cache cluster as preventive measure. <br />
💡 Use Hystrix, so in case a call fails, it returns default result so as to avoid cascaded failures.<br />


𝐈𝐒𝐒𝐔𝐄 3️⃣ : 𝐇𝐨𝐭𝐬𝐩𝐨𝐭 𝐝𝐚𝐭𝐚 𝐬𝐞𝐭 𝐢𝐬 𝐢𝐧𝐯𝐚𝐥𝐢𝐝. <br />
For very hot data, after expiry of cache TTL, the requests will bombard database between the time of expiry of TTL and re-cache.<br />
𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧:<br />
💡 When a hotspot data fails, only the first database query request is sent to the database, and all other query requests are blocked, thus protecting the database. That can be achieved with cache locks (mutex).<br />
💡 Set different TTLs to avoid simultaneous failures.<br />
