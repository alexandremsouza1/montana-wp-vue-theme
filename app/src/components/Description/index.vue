<template>
    <div class="route-service">
      <header class="service-header">
        <h1>Serviço de Roteamento OSRM</h1>
        <p class="service-description">
          Encontra a rota mais rápida entre coordenadas na ordem fornecida, oferecendo
          opções avançadas de personalização e retorno de dados.
        </p>
      </header>
  
      <section class="options-section">
        <h2>Opções Disponíveis</h2>
        <div class="options-grid">
          <div v-for="option in options" :key="option.name" class="option-card">
            <h3>{{ option.name }}</h3>
            <p>{{ option.description }}</p>
            <a :href="option.docLink" target="_blank" rel="noopener noreferrer" class="doc-link">
              Acesse a documentação
            </a>
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script>
  export default {
    name: 'RouteServiceDescription',
    data() {
      return {
        options: [
          {
            name: 'Rotas Alternativas',
            description: 'Busca rotas alternativas além da rota principal. Você pode especificar o número de rotas alternativas desejadas.',
            values: 'true, false, ou número específico',
            default: 'false',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Passos da Rota',
            description: 'Retorna instruções detalhadas passo a passo para cada segmento da rota.',
            values: 'true, false',
            default: 'false',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Anotações',
            description: 'Fornece metadados adicionais para cada coordenada ao longo da rota, incluindo nós, distância, duração, fontes de dados, peso e velocidade.',
            values: 'true, false, nodes, distance, duration, datasources, weight, speed',
            default: 'false',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Geometrias',
            description: 'Define o formato de retorno da geometria da rota, afetando tanto a visão geral quanto os passos individuais.',
            values: 'polyline, polyline6, geojson',
            default: 'polyline',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Visão Geral',
            description: 'Controla o nível de detalhe da geometria da rota na visão geral.',
            values: 'simplified, full, false',
            default: 'simplified',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Continuar em Linha Reta',
            description: 'Força a rota a manter-se em linha reta nos pontos de passagem, mesmo que um desvio seja mais rápido.',
            values: 'default, true, false',
            default: 'default',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          },
          {
            name: 'Pontos de Passagem',
            description: 'Permite especificar quais coordenadas devem ser tratadas como pontos de passagem na rota.',
            values: 'Índices das coordenadas no formato {index};{index};{index}...',
            default: 'Todas as coordenadas são tratadas como pontos de passagem',
            docLink: 'https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md#route-service'
          }
        ],
        responseDetails: [
          {
            name: 'Código',
            description: 'Indica o status da requisição (Ok para sucesso)'
          },
          {
            name: 'Waypoints',
            description: 'Array de objetos representando todos os pontos de passagem na ordem'
          },
          {
            name: 'Rotas',
            description: 'Array de objetos de rota, ordenados por ordem decrescente de recomendação'
          }
        ]
      }
    }
  }
  </script>
  
  <style scoped>
  .route-service {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
    font-family: system-ui, -apple-system, sans-serif;
  }
  
  .service-header {
    text-align: center;
    margin-bottom: 3rem;
  }
  
  h1 {
    color: #2c3e50;
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }
  
  .service-description {
    color: #666;
    font-size: 1.2rem;
    line-height: 1.6;
  }
  
  .options-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }
  
  .option-card {
    background: #f8f9fa;
    border-radius: 8px;
    padding: 1.5rem;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  
  h2 {
    color: #2c3e50;
    font-size: 1.8rem;
    margin-bottom: 1.5rem;
    border-bottom: 2px solid #eee;
    padding-bottom: 0.5rem;
  }
  
  h3 {
    color: #3498db;
    font-size: 1.3rem;
    margin-bottom: 1rem;
  }
  
  .option-values {
    margin-top: 1rem;
    font-size: 0.9rem;
  }
  
  .values-label, .default-label {
    font-weight: bold;
    color: #666;
    margin-right: 0.5rem;
  }
  
  .default-value {
    margin-top: 0.5rem;
    font-size: 0.9rem;
    color: #666;
  }
  
  .response-section {
    margin-top: 3rem;
  }
  
  .response-details ul {
    list-style: none;
    padding: 0;
  }
  
  .response-details li {
    margin-bottom: 1rem;
    padding: 1rem;
    background: #f8f9fa;
    border-radius: 6px;
  }
  
  .response-details strong {
    color: #3498db;
  }
  
  .doc-link {
    display: inline-block;
    margin-top: 1rem;
    padding: 0.5rem 1rem;
    background-color: #3498db;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    transition: background-color 0.3s ease;
  }
  
  .doc-link:hover {
    background-color: #2980b9;
  }
  </style>
  
  