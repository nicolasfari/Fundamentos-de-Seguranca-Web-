# Fundamentos-de-Seguranca-Web-

# Fundamentos de Segurança Web

## Descrição
Estudo sobre fundamentos de segurança em aplicações web, cobrindo tipos de ataques do lado do cliente e do servidor, funcionamento e criação de regras WAF



---

## Conceitos Abordados

### Componentes de uma aplicação web
Qualquer serviço web é composto por três partes principais:

- **Aplicação** — o código, imagens e estilos que definem o site
- **Servidor Web** — hospeda a aplicação e responde às requisições (Apache, Nginx, IIS)
- **Máquina Host** — o sistema operacional subjacente (Linux ou Windows)
  
---

## Ataques do lado do cliente
Exploram vulnerabilidades no navegador ou no comportamento do usuário. O SOC tem visibilidade limitada desses ataques pois ocorrem dentro do navegador da vítima — sem gerar tráfego HTTP visível.

| Ataque | Descrição |
|--------|-----------|
| XSS | Injeta scripts maliciosos em páginas web executados no navegador da vítima. Usado para roubar cookies e sessões |
| CSRF | Engana o navegador para enviar requisições não autorizadas em nome do usuário autenticado |
| Clickjacking | Sobrepõe elementos invisíveis ao conteúdo legítimo induzindo cliques maliciosos |

---

## Ataques do lado do servidor
Exploram vulnerabilidades no servidor, no código da aplicação ou no backend. Diferente dos ataques do lado do cliente, deixam rastros nos logs e no tráfego de rede.

| Ataque | Descrição |
|--------|-----------|
| SQL Injection | Insere código SQL malicioso em campos de formulário para manipular o banco de dados |
| Força Bruta | Testa múltiplas combinações de credenciais automaticamente |
| Directory Fuzzing | Varre diretórios e arquivos do servidor em busca de endpoints vulneráveis |

---
## WAF — Web Application Firewall

### O que é
O WAF inspeciona todo tráfego HTTP antes de chegar ao servidor, bloqueando requisições maliciosas com base em regras.

### Tipos de WAF
| Tipo | Descrição |
|------|-----------|
| Baseado em nuvem | Proxy reverso na frente do servidor. Ex: Cloudflare |
| Baseado em host | Instalado diretamente no servidor web |
| Baseado em rede | Dispositivo no perímetro da rede corporativa |

### Regras WAF
| Tipo de regra | Exemplo |
|---------------|---------|
| Bloquear ferramenta conhecida | IF User-Agent contains "sqlmap" → BLOCK |
| Bloquear IP malicioso | IF IP == 10.10.10.100 → BLOCK |
| Limitar tentativas de login | IF /login AND requests > 5/min → BLOCK |
| Desafio por região | IF Region != "BR" → CAPTCHA |

## Lições Aprendidas
- Ataques do lado do cliente ocorrem no navegador da vítima —
o SOC tem visibilidade limitada sem monitoramento de endpoint
- Ataques do lado do servidor deixam rastros em logs e tráfego de rede
- WAF baseado em User-Agent bloqueia ferramentas comuns de ataque
automatizado como sqlmap e Hydra
- Rate limiting no WAF previne ataques de força bruta
- Regras personalizadas no WAF permitem adaptar a proteção ao
contexto específico da aplicação

## Referências
- OWASP Top 10: https://owasp.org/www-project-top-ten/
- MITRE ATT&CK T1190: https://attack.mitre.org/techniques/T1190/
- MITRE ATT&CK T1595: https://attack.mitre.org/techniques/T1595/
- MITRE ATT&CK T1110: https://attack.mitre.org/techniques/T1110/
