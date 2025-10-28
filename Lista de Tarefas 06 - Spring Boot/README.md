# 🌟 Lista de Tarefas 06 — Spring Boot + Vue.js

## 👨‍💻 Autor
**Ruan da Silva Pereira**



## 🐞 1️⃣ Problema Encontrado
❌ Os títulos das tarefas não apareciam no frontend.  
⚠️ **Causa:** Dados de seed não carregavam devido ao bloqueio do **CORS** no backend.



## 🛠️ 2️⃣ Correção Realizada

### 🔹 Backend (Spring Boot)
Configuração de **CORS** adicionada para liberar acesso do frontend:

```java
@Configuration
public class WebConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("http://localhost:5173")
                        .allowedMethods("GET", "POST", "PUT", "DELETE");
            }
        };
    }
}
````
✅ Agora o frontend consegue acessar os dados do backend sem erros de CORS.

### 🔹 Frontend (Vue.js)
Ajuste no componente para exibir corretamente os títulos das tarefas:

````css
<span v-if="tarefaEditandoId !== tarefa.id"
>
{{ tarefa.titulo }}
</span>
````
✅ Títulos aparecem corretamente e a lista funciona normalmente.


---


## 🚀 3️⃣ Como Rodar
### 🔹 Backend
Abra o projeto Spring Boot no IDE.

Rode a aplicação **(ApiApplication.java).**

API disponível em: 
````
http://localhost:8088/api
````

---

### 🔹 Frontend
Entre na pasta do projeto Vue.

Instale dependências:

````terminal
npm install
````
Rode o servidor:
````
npm run dev
````
Acesse:
````
http://localhost:5173
````

---

### 📌 4️⃣ Funcionalidades Corrigidas
> 📝 Listar tarefas
>
> ➕ Adicionar novas tarefas
>
> ✏️ Editar título das tarefas
>
> ✅ Marcar como concluída
>
> ❌ Remover tarefas
>
> 🌐 Comunicação frontend-backend funcionando corretamente


---

### 📂 Observações Finais
> ✔️ Aplicação funcionando após correção do CORS
>
> ✔️ Todos os dados carregam corretamente
> 
> ✔️ Projeto pronto para entrega individual
