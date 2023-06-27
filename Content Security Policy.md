---
share: true  
---

De acordo com o artigo acima uma boa maneira de configurar o CSP para se defender de XSS seria se utilizar de Strict Content Security Policy que nada mais eh que CSP baseado em hash ou nonce para tags de script. Se utilizar de host-allowlist-based CSP não eh uma boa ideia já que eles podem ser [bypassed em muitas configurações](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/45542.pdf).

Uma boa pratica eh sempre configurar o default-src para ‘self’ ou ‘none’, pq ele serve de fallback para outras diretivas que possam nao ter sido configuradas.

![[Pasted image 20230627192332.png]]

CSP pode ser dividido em 3 categorias:

1. Restrição do carregamento de recursos.
    
    limitar a habilidade para carregar varios subrecursos pra um conjunto de hosts permitidos pelo desenvolvedor. Comumente usado como `script-src`, `style-src`, `img-src` e `default-src`.
    
2. Restricao de URL auxiliares.
    
    prevenir de quais hosts podemos carregar recursos. Usado com `frame-ancestors` , `base-uri` e `form-action` .
    
3. Conjunto de opcoes de confinamento e “endurecimento”(ferramentas para diminuir a vulnerabilidade em software)
    

CSP oferece protecao para 3 tipos de vulnerabilidade:

1. XSS
    
    Habilidade de injetar e executar scripts nao confiaveis em uma aplicacao vulneravel.
    
2. Clickjacking
    
    Forcar o usuario a tomar acoes indesejadas em uma aplicacao afetada pela sobreposicao de iframes ocultos
    
3. Mixed content
    
    Carregar recursos de protocolos inseguros em paginas fornecidas sobre https
    

> minimal Content Security Policy required for an Angular application is:

```json
Content-Security-Policy: default-src 'self'; style-src 'self' 'unsafe-inline';
```

---

## Csp Bypasses

<script defer="true" src="data:text/javascript,document.body.innerText=/hello/"></script>