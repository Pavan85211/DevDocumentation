### **Amazon CloudFront – AWS Interview Guide**  

Amazon **CloudFront** is a **Content Delivery Network (CDN)** that **delivers content (web pages, images, videos, APIs, etc.)** to users globally with low latency and high speed.  

---

## **1️⃣ Basic CloudFront Concepts**  

| **Concept** | **Description** |
|------------|----------------|
| **CDN** | A globally distributed network that caches content closer to users. |
| **Edge Location** | Data centers that store cached content for faster delivery. |
| **Origin** | The original source of the content (e.g., S3, EC2, or on-prem servers). |
| **Distribution** | A CloudFront setup that routes user requests to edge locations. |
| **Cache Behavior** | Rules to control caching, compression, and HTTP methods. |
| **TTL (Time-To-Live)** | Defines how long content is cached at edge locations. |
| **Invalidation** | Used to clear outdated content from CloudFront caches. |

---

## **2️⃣ Key AWS CloudFront Features**  

| **Feature** | **Description** |
|------------|----------------|
| **Global Edge Network** | CloudFront has multiple edge locations worldwide for faster delivery. |
| **Origin Shield** | Provides additional caching layer to reduce load on the origin server. |
| **Field-Level Encryption** | Encrypts sensitive data before sending it to an origin. |
| **Lambda@Edge** | Runs serverless code at edge locations to customize responses. |
| **Signed URLs & Cookies** | Restricts access to content using security tokens. |
| **DDoS Protection** | Built-in security with AWS Shield Standard. |

---

## **3️⃣ Common CloudFront Interview Questions & Answers**  

### **🔹 Q1: What is Amazon CloudFront, and how does it work?**  
✅ **Answer:**  
Amazon CloudFront is a **Content Delivery Network (CDN)** that caches content across multiple **edge locations** worldwide.  
- When a user requests content, CloudFront **checks the cache** at the nearest edge location.  
- If content is cached, it is **served directly** (low latency).  
- If not, CloudFront **fetches** content from the **origin** (e.g., S3, EC2, or an on-premise server).  
- The content is **cached** at the edge location for future requests.  

---

### **🔹 Q2: What are the key components of CloudFront?**  
✅ **Answer:**  
1. **Origin** – Source of content (S3, EC2, API Gateway, on-prem servers).  
2. **Edge Locations** – AWS data centers that cache content closer to users.  
3. **Distributions** – A CloudFront setup that routes traffic from origin to users.  
4. **Cache Behavior** – Rules for caching, request methods, and security.  
5. **TTL (Time-To-Live)** – Defines how long content is cached before refreshing.  

---

### **🔹 Q3: What are the benefits of using CloudFront?**  
✅ **Answer:**  
- **Low Latency & High Performance** – Content is cached at edge locations for faster delivery.  
- **Scalability** – Handles high traffic automatically.  
- **Cost Savings** – Reduces data transfer costs from origins (S3, EC2).  
- **Security** – Protects against DDoS attacks with AWS Shield and IAM-based restrictions.  
- **Integration with AWS Services** – Works with S3, EC2, Lambda@Edge, and WAF.  

---

### **🔹 Q4: What is the difference between CloudFront and S3?**  
✅ **Answer:**  
| Feature | CloudFront | S3 |
|---------|-----------|----|
| Purpose | CDN for caching & content delivery | Object storage for files, images, backups |
| Performance | Serves content from the nearest edge location | Retrieves files from a central bucket |
| Security | Supports signed URLs, IAM, AWS WAF | IAM permissions & bucket policies |
| Cost | Reduces S3 data transfer costs | Charges per request & storage size |

💡 **Tip:** CloudFront is often used in front of **S3** to improve performance.

---

### **🔹 Q5: How does CloudFront handle security?**  
✅ **Answer:**  
- **Signed URLs & Cookies** – Restrict content access to authorized users.  
- **AWS Shield** – Protects against **DDoS attacks**.  
- **AWS WAF** – Blocks malicious traffic using security rules.  
- **Origin Access Control (OAC)** – Ensures that only CloudFront can access an S3 bucket (replacing Origin Access Identity - OAI).  

---

### **🔹 Q6: How can you clear cached content in CloudFront?**  
✅ **Answer:**  
Use **CloudFront Invalidation** to remove outdated files:  
```sh
aws cloudfront create-invalidation --distribution-id EXAMPLE123 --paths "/index.html"
```
- This forces CloudFront to fetch new content from the origin.  
- **⚠️ Note:** Invalidations **cost money**, so use cache versioning (`index-v2.html`) instead.  

---

### **🔹 Q7: What is the difference between CloudFront and a traditional Load Balancer?**  
✅ **Answer:**  
| Feature | CloudFront | Load Balancer (ALB, NLB) |
|---------|-----------|-------------------------|
| Purpose | Caches & delivers static/dynamic content | Distributes traffic among backend servers |
| Caching | ✅ Yes (reduces origin load) | ❌ No caching |
| Performance | ✅ Faster (content served from edge) | ⚡ Fast, but depends on backend latency |
| Integration | Works with S3, Lambda@Edge | Works with EC2, ECS, Fargate |
| Security | Signed URLs, AWS WAF | IAM, TLS, WAF |

💡 **Tip:** CloudFront **works with** ALB/NLB for global traffic distribution.

---

### **🔹 Q8: What is Lambda@Edge in CloudFront?**  
✅ **Answer:**  
**Lambda@Edge** allows you to run **serverless functions** (AWS Lambda) at CloudFront edge locations to modify requests and responses.  

💡 **Example Use Cases:**  
- **Redirect HTTP to HTTPS**  
- **Add custom headers** for security  
- **Compress responses** to reduce data transfer  

**Example Lambda@Edge function (JavaScript) to redirect HTTP to HTTPS:**
```javascript
exports.handler = async (event) => {
    const response = event.Records[0].cf.response;
    response.headers['strict-transport-security'] = [{key: 'Strict-Transport-Security', value: 'max-age=31536000; includeSubDomains'}];
    return response;
};
```

---

### **🔹 Q9: What is the difference between CloudFront and API Gateway?**  
✅ **Answer:**  
| Feature | CloudFront | API Gateway |
|---------|-----------|------------|
| Purpose | Caches & accelerates content | Manages REST & WebSocket APIs |
| Use Case | Web pages, images, videos | Microservices, API management |
| Caching | ✅ Yes | ⚡ Optional |
| Security | IAM, WAF, Signed URLs | IAM, JWT, API keys |
| Latency | ✅ Low (Edge locations) | ⚡ Slightly higher (regional APIs) |

💡 **Tip:** CloudFront is **often used with** API Gateway to cache API responses.

---

### **🔹 Q10: When should you NOT use CloudFront?**  
✅ **Answer:**  
Avoid CloudFront if:  
❌ You don’t need global distribution (use ALB instead).  
❌ Your content **changes frequently** (high invalidation costs).  
❌ You need **real-time** streaming (use AWS Media Services instead).  

---

## **Final Interview Tips 🎯**  
✅ Be ready to **explain CloudFront’s caching, security, and integrations**.  
✅ **Know when to use CloudFront vs. ALB, API Gateway, or S3**.  
✅ If asked about **cost**, mention:  
   - **Requests-based pricing** (GET/POST).  
   - **Data transfer out costs**.  
   - **Invalidation costs** (avoid frequent cache invalidations).  
✅ Prepare **real-world use cases** (e.g., CDN for a website, caching API responses).  

---

🚀 **Let me know if you need more interview questions or hands-on examples!**