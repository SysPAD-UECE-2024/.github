# Sistema de Proteção de Dados Baseado em Técnicas de Criptografia e Anonimização

Este projeto apresenta um sistema integrado de proteção de dados que combina técnicas de criptografia e anonimização para garantir privacidade e segurança de informações. Desenvolvido pelo Laboratório de Redes de Computadores e Segurança (LARCES/UECE), o artefato consiste em três componentes principais:
1. **Syspad API**: API RESTful para processamento de dados
2. **Front-end**: Interface web para interação com o sistema
3. **Database Monitor Agent**: Agente de monitoramento de operações em banco de dados

Implantado em ambiente de nuvem, o sistema oferece alta capacidade de processamento sem sobrecarregar recursos locais, atendendo aos requisitos de legislações como LGPD e GDPR.

## Estrutura do Repositório
```
├── agent/               # Agente de monitoramento de banco de dados
├── back-end/            # Implementação da API RESTful
├── front-end/           # Interface web (Quasar/Vue.js)
├── docs/                # Documentação técnica e manuais
└── README.md            # Este arquivo
```

# Selos Considerados
Os selos considerados são: **Disponíveis**, **Funcionais**, **Sustentáveis** e **Reprodutíveis**.

# Informações Básicas

## Requisitos de Hardware
- Mínimo: 1GB RAM, 2 vCPUs (ambiente local)
- Recomendado: Configuração escalável em cloud (AWS/GCP/Azure equivalentes)

## Ambiente de Software
- **Sistema Operacional**: Linux/Windows/macOS (testado em Ubuntu 22.04 LTS)
- **Runtime**: Python 3.9+, Node.js 16.x
- **Serviços Cloud**: Compatível com principais provedores (AWS, Azure, GCP)

# Dependências

## Principais Tecnologias
| Componente       | Versão   | Finalidade                          |
|------------------|----------|-------------------------------------|
| Python           | 3.10+    | Back-end e agentes                  |
| Flask            | 2.3.2    | Framework web para APIs             |
| Quasar           | 2.12.0   | Framework front-end                 |
| Vue.js           | 3.3.4    | Biblioteca front-end                |
| SQLAlchemy       | 2.0.23   | ORM para acesso a bancos de dados   |
| Docker           | 24.0+    | Containerização de serviços         |


# Preocupações com Segurança
- 🔒 Utilize ambiente isolado para testes de produção
- 🔑 Mantenha as chaves de criptografia em variáveis de ambiente
- 🛡️ Revogue credenciais de teste após avaliação
- ⚠️ Nunca utilize credenciais reais em ambientes de teste

# Instalação

## Pré-requisitos Globais
```bash
# Instale o gerenciador de pacotes do seu sistema
sudo apt-get update && sudo apt-get install -y git python3-pip nodejs npm docker.io

# Verifique as versões
python3 --version  # Deve retornar 3.10+
node --version     # Deve retornar v16.x+
docker --version   # Deve retornar 24.0+
```

## 1. Agente de Monitoramento
### Opção A: Instalação Manual
```bash
git clone https://github.com/FRIDA-LACNIC-UECE/agent.git
cd agent
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Configurar variáveis (adaptar conforme ambiente)
export FLASK_APP=application.py
export API_URL=http://localhost:5000
export SECRET_KEY='chave-secreta-aleatoria'

flask run --port=3000
```

### Opção B: Via Docker
```bash
docker compose -f docker-compose-agent.yml up --build
```

## 2. Back-end (API)
```bash
git clone https://github.com/FRIDA-LACNIC-UECE/back-end.git
cd back-end

# Configurar ambiente
cp .env.example .env  # Editar com suas credenciais

# Iniciar serviço
docker compose up --build -d
```

## 3. Front-end
```bash
git clone -b main https://github.com/FRIDA-LACNIC-UECE/front-end.git
cd front-end

npm install
quasar dev
```

# Teste mínimo

Para realizar um teste mínimo, execute os seguintes passos:
1. Submeta um conjunto de dados de teste através da API.
2. Verifique a resposta com dados anonimizados e criptografados.
3. Observe o registro de operações pelo Database Monitor Agent.

# Experimentos

Os experimentos estão estruturados para validar as reivindicações do artigo. Cada experimento possui uma subseção detalhando:
- Arquivos de configuração a serem alterados
- Comandos a serem executados
- Flags e parâmetros necessários
- Tempo esperado de execução e recursos utilizados (ex.: 1GB de RAM/Disk)
- Resultado esperado para cada cenário
  
# Licença
Este projeto não está sob nenhuma licença específica, portanto, pode ser utilizado livremente, sem restrições. Use-o conforme desejar.
