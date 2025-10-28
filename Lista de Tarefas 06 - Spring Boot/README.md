📝 Lista de Tarefas 06 - Spring Boot + Vue.js
https://img.shields.io/badge/Java-17-orange
https://img.shields.io/badge/Spring%2520Boot-3.0-green
https://img.shields.io/badge/Vue.js-3.0-brightgreen
https://img.shields.io/badge/MySQL-8.0-blue

👨‍💻 Autor
Felipe Paião Ferreira

🐞 Problema Encontrado
❌ Situação Inicial
Os títulos das tarefas não apareciam no frontend após o carregamento da aplicação.

⚠️ Causa Identificada
Bloqueio de CORS (Cross-Origin Resource Sharing) no backend impedia o frontend de acessar os dados da API. Os dados de seed não carregavam devido à política de segurança do navegador.

Erro no console:

text
Access to XMLHttpRequest at 'http://localhost:8088/api/tarefas' from origin 'http://localhost:5173' 
has been blocked by CORS policy
🛠️ Correção Realizada
🔹 Backend (Spring Boot)
Configuração de CORS adicionada para liberar acesso do frontend:

java
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
✅ Resultado: Agora o frontend consegue acessar os dados do backend sem erros de CORS.

🔹 Frontend (Vue.js)
Ajuste no componente para exibir corretamente os títulos das tarefas:

vue
<span v-if="tarefaEditandoId !== tarefa.id">
  {{ tarefa.titulo }}
</span>
✅ Resultado: Títulos aparecem corretamente e a lista funciona normalmente.

🚀 Como Executar a Aplicação
🔹 Backend (Spring Boot)
Abra o projeto Spring Boot na sua IDE

Execute a aplicação principal: ApiApplication.java

API estará disponível em: http://localhost:8088/api

🔹 Frontend (Vue.js)
Navegue até a pasta do projeto Vue:

bash
cd frontend
Instale as dependências:

bash
npm install
Execute o servidor de desenvolvimento:

bash
npm run dev
Acesse a aplicação em: http://localhost:5173

📌 Funcionalidades Corrigidas
✅ Listar tarefas - Agora exibe todos os dados corretamente

✅ Adicionar novas tarefas - Funcionamento completo

✅ Editar título das tarefas - Interface corretamente implementada

✅ Marcar como concluída - Estado visual atualizado

✅ Remover tarefas - Exclusão funcionando

✅ Comunicação frontend-backend - Integração total sem erros de CORS

🛠️ Tecnologias Utilizadas
Backend
Java 17

Spring Boot 3.0

Spring Data JPA

MySQL Database

Maven

Frontend
Vue.js 3.0

Axios (para requisições HTTP)

Vite (ambiente de desenvolvimento)

📊 Estrutura da API
Método	Endpoint	Descrição
GET	/api/tarefas	Lista todas as tarefas
POST	/api/tarefas	Cria uma nova tarefa
PUT	/api/tarefas/{id}	Atualiza uma tarefa
DELETE	/api/tarefas/{id}	Exclui uma tarefa
