# ![DevSuperior logo](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/devsuperior-logo-small.png) Projeto DSMeta
>  *Aplicação com as tecnologias mais demandadas do mercado*

<div align="center">
<img src="https://user-images.githubusercontent.com/72041260/179550925-b0f69988-beec-4345-9c7c-8230727f8e53.gif" />
</div>

## Tecnologias utilizadas
- Java 
- JavaScript 
- Springboot 
- React 
- Html 
- CSS 

## Detalhes
- Projetos backend e frontend
- Projeto salvo no Github em monorepo
- Visual estático front end



## Processo de Criação do Spring Boot

- Projeto Spring Boot criado  no `Spring Initializr` com as seguintes dependências:
  - Web
  - JPA
  - H2
  - Security

- Ajuste no arquivo pom.xml:


## Salvar primeira versão no Github


```bash
git init

git add .

git commit -m "Project created"

git branch -M main

git remote add origin git@github.com:seuusuario/seurepositorio.git

git push -u origin main
```


```
yarn add react-datepicker@4.8.0 @types/react-datepicker@4.4.2
```

```javascript
import DatePicker from "react-datepicker";
import "react-datepicker/dist/react-datepicker.css";
```

```javascript
<DatePicker
    selected={new Date()}
    onChange={(date: Date) => {}}
    className="dsmeta-form-control"
    dateFormat="dd/MM/yyyy"
/>
```

## React Hook useState para manter estado das datas


```javascript
const date = new Date(new Date().setDate(new Date().getDate() - 365));
```

## BACK END
- Implementar o back end
- Acesso a banco de dados
- Criar endpoints da API REST
- Integração com SMS
- Implantação na nuvem


## Ferramentas

- Postman 
- Heroku CLI 

## Configuração de Segurança

```java
import java.util.Arrays;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.web.cors.CorsConfiguration;
import org.springframework.web.cors.CorsConfigurationSource;
import org.springframework.web.cors.UrlBasedCorsConfigurationSource;

@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		
		http.headers().frameOptions().disable();
		http.cors().and().csrf().disable();
		http.sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS);
		http.authorizeHttpRequests((auth) -> auth.anyRequest().permitAll());

		return http.build();
	}

	@Bean
	CorsConfigurationSource corsConfigurationSource() {
		CorsConfiguration configuration = new CorsConfiguration().applyPermitDefaultValues();
		configuration.setAllowedMethods(Arrays.asList("POST", "GET", "PUT", "DELETE", "OPTIONS"));
		final UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
		source.registerCorsConfiguration("/**", configuration);
		return source;
	}
}
```

### Banco de Dados

- Criar entidade Sale
- Fazer mapeamento objeto-relacional (JPA)
- Configurar dados de conexão do banco de dados H2
- Fazer seed do banco de dados

### Teste de endpoint da API REST

- Criar repository
- Criar service
- Criar controller

### Consulta por data

Consulta customizada:

```java
@Query("SELECT obj FROM Sale obj WHERE obj.date BETWEEN :min AND :max ORDER BY obj.amount DESC")
Page<Sale> findSales(LocalDate min, LocalDate max, Pageable pageable);
```

### Envio de SMS

Dependências Maven do Twilio
```xml
<dependency>
	<groupId>com.twilio.sdk</groupId>
	<artifactId>twilio</artifactId>
	<version>8.31.1</version>
</dependency>
```

Variáveis de ambiente no application.properties:
```
twilio.sid=${TWILIO_SID}
twilio.key=${TWILIO_KEY}
twilio.phone.from=${TWILIO_PHONE_FROM}
twilio.phone.to=${TWILIO_PHONE_TO}
```

### Implantação no Heroku

Arquivo `system.properties`
```
java.runtime.version=17
```

- Criar app no Heroku
- Definir variáveis de ambiente:
  - TWILIO_SID
  - TWILIO_KEY
  - TWILIO_PHONE_FROM
  - TWILIO_PHONE_TO

```bash
heroku -v
heroku login
heroku git:remote -a <nome-do-app>
git remote -v
git subtree push --prefix backend heroku main
```

## Integração e Implementação
- Integrar back end e front end
- Implantar o front end


## Primeira requisição com Axios e useEffect

```
yarn add axios@0.27.2
```

## Listagem de vendas

Definição da BASE_URL:

```javascript
export const BASE_URL = import.meta.env.VITE_BACKEND_URL ?? "http://localhost:8080";
```


- **Passando as datas como argumento**

- **Enviar notificação**

- **Mensagem Toast de confirmação**


```
yarn add react-toastify@9.0.5
```

## No App.tsx:
```javascript
import { ToastContainer } from 'react-toastify';
import 'react-toastify/dist/ReactToastify.css';
```


## Passo: Deploy no Netlify


- Deploy básico
  - Base directory: frontend
  - Build command: yarn build
  - Publish directory: frontend/dist
  - Variáveis de ambiente:
    - VITE_BACKEND_URL
