# Introdução
A observabilidade de aplicações .NET utilizando o OpenTelemetry é uma técnica avançada projetada para oferecer insights profundos sobre o desempenho e a saúde das aplicações. Este documento explora os conceitos centrais da observabilidade, as abordagens específicas para aplicações .NET, o papel do OpenTelemetry e como essas práticas são implementadas no ecossistema .NET.

# O que é Observabilidade?
Observabilidade é a capacidade de entender o estado interno de um sistema ou aplicação a partir dos dados de telemetria que ele gera - logs, métricas e rastreamentos distribuídos, também conhecidos como os três pilares da observabilidade. Diferentemente da depuração, a observabilidade é não-invasiva e visa minimizar seu impacto no desempenho da aplicação.

# Logs
Registros cronológicos das operações do sistema, como erros ou operações de entrada.

# Métricas
Medições quantitativas, como número de solicitações processadas ou a latência das transações.

# Rastreamento Distribuído
Acompanha a jornada das solicitações através de componentes distribuídos, ajudando na identificação da origem dos problemas.

# Abordagens de Observabilidade no .NET
A observabilidade em aplicações .NET pode ser alcançada de três maneiras principais:

1. **Codificação Explícita:** Incorporando bibliotecas de observabilidade, como o OpenTelemetry, diretamente no código-fonte.
2. **Fora do Processo:** Utilizando ferramentas como o dotnet-monitor para coletar telemetria sem alterar o código-fonte.
3. **Gancho de Inicialização:** Injetando assemblies no processo que habilitam a coleta de instrumentação.

# O que é o OpenTelemetry?

OpenTelemetry é um padrão aberto e multiplataforma focado na geração, coleta e exportação de dados de telemetria. Ele oferece:

**APIs para Bibliotecas:** Permite a gravação de telemetria durante a execução do código.  
**APIs para Desenvolvedores de Aplicativos:** Configura o envio de telemetria para os back-ends.  
**Convenções Semânticas:** Diretrizes sobre nomenclatura e conteúdo dos dados telemétricos.  
**Interface para Exportadores:** Plug-ins que transmitem dados telemétricos para sistemas de   monitoramento.

Além disso, o OpenTelemetry oferece suporte ao protocolo OTLP, um meio agnóstico de transmitir dados de telemetria.

# Implementação .NET do OpenTelemetry

Especificamente no .NET, o OpenTelemetry interage diretamente com as APIs de telemetria já presentes no framework, como Microsoft.Extensions.Logging.ILogger para logs, System.Diagnostics.Metrics.Meter para métricas, e System.Diagnostics.ActivitySource para rastreamento distribuído. Assim, simplifica a coleta e exportação de telemetria, usando padrões comuns e facilitando a interoperabilidade com sistemas APM.

# Pacotes do OpenTelemetry no .NET

Os principais pacotes NuGet do OpenTelemetry categorizam-se em:

**API Principal:** Fornece a funcionalidade base.
**Instrumentação:** Coleta dados do ambiente de execução e bibliotecas comuns.
**Exportadores:** Facilita a comunicação com sistemas APM como Prometheus, Jaeger e OTLP.

# Exemplo Prático: Integrando com Prometheus, Grafana e Jaeger

**Configuração Inicial:** Criação de um projeto ASP.NET Core e inclusão de pacotes do OpenTelemetry.   
**Definições de Métricas e Atividades:** Definição de métricas ('greetings.count') e fontes de atividade customizadas.   
**Exportação de Telemetria:** Configuração do OpenTelemetry para coletar e exportar dados para o Prometheus e Jaeger.   
**Visualização de Métricas:** Utilização do Grafana para criar dashboards a partir dos dados coletados pelo Prometheus.    
**Rastreamento Distribuído com Jaeger:** Análise e visualização do fluxo de solicitações entre serviços.