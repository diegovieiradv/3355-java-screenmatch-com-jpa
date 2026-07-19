# Screenmatch com JPA

API REST para catalogo de series de TV que consome a OMDb API e persiste dados no PostgreSQL.

## Descricao

Aplicacao Spring Boot que busca dados de series na OMDb API, traduz sinopses para portugues via LibreTranslate, persiste no PostgreSQL e expoe endpoints REST para consulta.

## Funcionalidades

- Busca de dados de series na OMDb API
- Traducao de sinopses (LibreTranslate)
- Persistencia com JPA/Hibernate no PostgreSQL
- Endpoints REST para listar series, top 5, lancamentos
- Filtrar por categoria e temporadas
- CORS configurado para frontend

## Tecnologias

- **Linguagem:** Java 17
- **Framework:** Spring Boot 3.1.1
- **ORM:** Spring Data JPA
- **Banco de Dados:** PostgreSQL
- **Traducao:** LibreTranslate API
- **API Externa:** OMDb API
- **Build:** Maven

## Como Rodar

```bash
# Crie o banco PostgreSQL
CREATE DATABASE alura_series;

# Configure as variaveis de ambiente (src/.env)
DB_URL=jdbc:postgresql://localhost:5432/alura_series
DB_USER=postgres
DB_PASSWORD=sua_senha

# Execute
./mvnw spring-boot:run
```

## Endpoints

| Metodo | Rota | Descricao |
|--------|------|-----------|
| GET | /series | Listar todas as series |
| GET | /series/top5 | Top 5 series por avaliacao |
| GET | /series/lancamentos | Ultimos lancamentos |
| GET | /series/{id} | Detalhes de uma serie |
| GET | /series/{id}/temporadas/todas | Todas as temporadas |
| GET | /series/{id}/temporadas/{numero} | Episodios de uma temporada |
| GET | /series/categoria/{genero} | Filtrar por genero |

## Estrutura

```
src/main/java/.../
├── controller/    # SerieController
├── service/       # SerieService, ConsumoApi, ConverteDados
├── repository/    # SerieRepository
├── model/         # Serie, Episodio, Categoria, DTOs
├── config/        # Configuracao CORS
└── principal/     # CLI legado (comentado)
```

## Licenca

MIT License - Diego Vieira
