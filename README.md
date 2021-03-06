# API_Reste_Curso_Alura

01 - Paginação e ordenação de recursos:
Para realizar paginação com Spring Data JPA, devemos utilizar a interface Pageable;
Nas classes Repository, os métodos que recebem um pageable como parâmetro retornam objetos do tipo Page<>, ao invés de List<>;
Para o Spring incluir informações sobre a paginação no JSON de resposta enviado ao cliente da API, devemos alterar o retorno do método do controller de List<> para Page<>;
Para fazer a ordenação na consulta ao banco de dados, devemos utilizar também a interface Pageable, passando como parâmetro a direção da ordenação, utilizando a classe Direction, e o nome do atributo para ordenar;
Para receber os parâmetros de ordenação e paginação diretamente nos métodos do controller, devemos habilitar o módulo SpringDataWebSupport, adicionando a anotação @EnableSpringDataWebSupport na classe ForumApplication.

02 - Melhorando desempenho com Spring Cache
Para utilizar o módulo de cache do Spring Boot, devemos adicioná-lo como dependência do projeto no arquivo pom.xml;
Para habilitar o uso de caches na aplicação, devemos adicionar a anotação @EnableCaching na classe ForumApplication;
Para que o Spring guarde o retorno de um método no cache, devemos anotá-lo com @Cacheable;
Para o Spring invalidar algum cache após um determinado método ser chamado, devemos anotá-lo com @CacheEvict;
Devemos utilizar cache apenas para as informações que nunca ou raramente são atualizadas no banco de dados.

03 - Proteção com Spring Securiy
Para utilizar o módulo do Spring Security, devemos adicioná-lo como dependência do projeto no arquivo pom.xml;
Para habilitar e configurar o controle de autenticação e autorização do projeto, devemos criar uma classe e anotá-la com @Configuration e @EnableWebSecurity;
Para liberar acesso a algum endpoint da nossa API, devemos chamar o método http.authorizeRequests().antMatchers().permitAll() dentro do método configure(HttpSecurity http), que está na classe SecurityConfigurations;
O método anyRequest().authenticated() indica ao Spring Security para bloquear todos os endpoints que não foram liberados anteriormente com o método permitAll();
Para implementar o controle de autenticação na API, devemos implementar a interface UserDetails na classe Usuario e também implementar a interface GrantedAuthority na classe Perfil;
Para o Spring Security gerar automaticamente um formulário de login, devemos chamar o método and().formLogin(), dentro do método configure(HttpSecurity http), que está na classe SecurityConfigurations;
A lógica de autenticação, que consulta o usuário no banco de dados, deve implementar a interface UserDetailsService;
Devemos indicar ao Spring Security qual o algoritmo de hashing de senha que utilizaremos na API, chamando o método passwordEncoder(), dentro do método configure(AuthenticationManagerBuilder auth), que está na classe SecurityConfigurations.
