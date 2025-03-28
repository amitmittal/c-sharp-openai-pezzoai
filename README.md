Here’s a **README.md** file for the GitHub repository of the console application:  

---

# 🚀 PezzoAI Integration with OpenAI .NET SDK  

This project demonstrates how to integrate **PezzoAI** with **OpenAI's official C# SDK** to:  
✔ Inject **custom headers** for PezzoAI authorization  
✔ Configure **dynamic endpoints** with fallback to OpenAI  
✔ Optimize performance using **prompt caching**  
✔ Implement a **C# console application** showcasing the integration  

---

## 📌 Features  

- **Custom Header Injection:** Adds PezzoAI headers (`X-Pezzo-Api-Key`, `X-Pezzo-Project-Id`, `X-Pezzo-Environment`).  
- **Dynamic Endpoint Configuration:** Uses PezzoAI as the primary API and falls back to OpenAI if PezzoAI fails.  
- **Prompt Caching:** Reduces redundant API calls for frequently used prompts.  
- **Console App Implementation:** Provides a simple example to test PezzoAI with OpenAI in **.NET Core**.  

---

## 📦 Installation  

1️⃣ **Clone the repository**  
```sh
git clone https://github.com/amitmittal/c-sharp-openai-pezzoai.git
cd c-sharp-openai-pezzoai
```

2️⃣ **Install OpenAI .NET SDK**  
```sh
dotnet add package OpenAI --version 2.0.0-beta.11
```

3️⃣ **Build and run the project**  
```sh
dotnet run
```

---

## 🛠 Configuration  

Edit the **API key and PezzoAI endpoint settings** in the `GetOpenAIclient` method inside `Program.cs`:  

```csharp
private static OpenAIClient GetOpenAIclient()
{
    var options = new OpenAIClientOptions();
    options.Endpoint = new Uri("https://pezzoai.example.com"); // Replace with your PezzoAI URL
    options.AddPolicy(CreateAddPezzoHeaderPolicy(), PipelinePosition.PerCall);

    return new OpenAIClient("your-pezzoai-api-key", options);
}
```

Set up the **header injection policy**:  

```csharp
private static PipelinePolicy CreateAddPezzoHeaderPolicy()
{
    return new PezzoPipelinePolicy((message) =>
    {
        message.Request.Headers.Set("X-Pezzo-Api-Key", "pez_4bc0000");
        message.Request.Headers.Set("X-Pezzo-Project-Id", "cm2g710000");
        message.Request.Headers.Set("X-Pezzo-Environment", "Production");
    });
}
```

---

## 🚀 Running the Console App  

Run the application with:  

```sh
dotnet run
```

Expected output:  
- **If PezzoAI is available:** Fetches response via PezzoAI.  
- **If PezzoAI fails:** Falls back to OpenAI API.  
- **If the prompt is cached:** Uses cached response instead of making an API call.  

---

## 📖 Learn More  

Check out the full tutorial:  
🔗 **[How to Set Custom Headers and Endpoint for Using PezzoAI Proxy with OpenAI’s C# SDK](https://amitmittal.tech/how-to-set-custom-headers-and-endpoint-for-using-pezzoai-proxy-with-openais-official-c-sdk/)**  

---

## 🛡 License  

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.  

---

## 👨‍💻 Author  

Developed by **Amit Mittal**. Connect with me on [LinkedIn](https://www.linkedin.com/in/bitssmittal/). 🚀  

---

This **README.md** provides a structured, professional, and SEO-friendly guide for developers. Let me know if you'd like any refinements! 😊
