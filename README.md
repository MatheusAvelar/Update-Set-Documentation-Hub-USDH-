 📘 Update Set Documentation Hub (USDH)

**Documentação automatizada, inteligente e integrada para Update Sets no ServiceNow.**

O **Update Set Documentation Hub (USDH)** é uma solução completa desenvolvida para gerar documentação **técnica e funcional** de Update Sets de forma automática no ServiceNow.  
Ele unifica **artefatos**, **evidências visuais**, **Instance Scan**, **descrições** e **links diretos** em uma única visão clara, organizada e pronta para exportação.

Ideal para **desenvolvedores**, **QAs**, **arquitetos**, **POs** e **equipes de governança**, reduzindo esforço manual e padronizando entregas.

---

## 🎯 Objetivo
- Automatizar a documentação de Update Sets  
- Padronizar entregas técnicas e funcionais  
- Reduzir esforço manual e retrabalho  
- Melhorar governança, auditoria e rastreabilidade  
- Facilitar a comunicação entre áreas técnicas e de negócio  

---

## 🚀 Funcionalidades Principais

### 🔧 1. Geração Automática de Documentação
Script Include dedicado: **`GetUpdateSetDocumentation`**

Gera **HTML completo** com:
- Lista de artefatos por tipo  
- Nome amigável do item  
- Descrição técnica  
- Status da alteração (**criação, atualização, exclusão**)  
- Link direto para o registro no ServiceNow  
- Ícones por tipo (com fallback seguro sem emojis)  
- Tradutor de tipos para linguagem amigável para POs  
- Título dinâmico baseado no cenário de teste  

---

### 📄 2. UI Page Moderna e Intuitiva
Interface construída com **Jelly + Client Script**, incluindo:

- Campo para nome do Update Set  
- Seleção do público (**Dev / PO**)  
- Botão ⚙️ **Gerar Documentação**  
- Botão 💾 **Exportar PDF**  
- Botão 📎 **Anexar Imagens**  
- Pré-visualização de evidências  

**Inputs adicionais:**
- Projeto  
- Squad  
- Story  
- Cenário  
- Ambiente  
- Observações  

---

### 📸 3. Gerenciamento de Evidências
- Upload de imagens (**PNG, JPG, GIF**)  
- Campo de descrição por imagem  
- Preview antes da exportação  
- Validação do tipo de arquivo  
- Área de anexos exibida **somente após a geração da documentação**  

---

### 🧠 4. Integração com Instance Scan
Incluído diretamente na documentação:
- Scans relacionados ao Update Set  
- Status (**complete / failed**)  
- Findings detectados  
- Contagem total  
- Severidade destacada por cor  
- Links diretos para o registro  
- Expansão e contração de detalhes  

---

### 🗂️ 5. Tipos de Artefatos Suportados

#### 🧠 Back-end
- Script Include  
- Business Rule  
- Fix Script  
- Scheduled Job  
- Flow  
- REST API  
- Transform Map  
- ACL  

#### 🌍 Front-end
- UI Page  
- UI Action  
- Client Script  
- Field Label  
- Widget  
- Dashboard  

#### 🔗 Integrações
- REST Message  
- SOAP Message  
- IntegrationHub  
- Spokes  

#### 📦 Outros
- Update Set  
- System Property  
- Style Sheet  
- Email Template  
- Knowledge Article  
- SLA  
- Report  

---

## ⚙️ Arquitetura Técnica

### 🧩 Script Include – `GetUpdateSetDocumentation`

**Métodos principais:**

| Método | Função |
|------|------|
| `getDocumentation()` | Gera o HTML completo da documentação |
| `getDescriptionByType()` | Retorna a descrição técnica do item |
| `getFriendlyName()` | Formata o nome amigável |
| `getIconByType()` | Retorna ícone / emoji / SVG do tipo |
| `getTranslatedTypeName()` | Tradução técnica para perfil PO |
| `getRecordLink()` | Gera link direto para o registro |

---

### 🎨 UI Page
- Jelly + Client Script  
- Design moderno e responsivo  
- Preview em tempo real  
- Exportação para PDF  
- Validações e alertas amigáveis  

---

## ⚠️ Observações Importantes

### ❗ Uso de emojis como ícones
Alguns ambientes podem apresentar:
- Erros de codificação UTF-8  
- HTML quebrado  
- `GlideAjax` retornando vazio  
- Incompatibilidade com instâncias mais antigas  

**✔️ Soluções recomendadas**
- Ativar fallback sem emojis  
- Utilizar SVG inline  
- Implementar `try/catch` no método de ícones  
- Flag de controle: `useIcons = false`  

---

### ❗ System Property obrigatória – `doc.uri`

Para que os **links diretos para os registros** funcionem corretamente, é **obrigatória** a configuração da seguinte **System Property**:

- **Nome:** `doc.uri`  
- **Tipo:** String  
- **Valor:** URL base da instância  
  - Exemplo: `https://sua_instancia.service-now.com`

Essa propriedade é utilizada no **Script Include `GetUpdateSetArtifacts`**, conforme o trecho:

```javascript
var instanceUrl = gs.getProperty('doc.uri');

📌 **Caso essa propriedade não esteja configurada**, os links gerados poderão ficar **incompletos ou inválidos**.

---

### ❗ Importação obrigatória da tabela – `Table Artefatos.xml`

Para o correto funcionamento do **Update Set Documentation Hub (USDH)**, é **obrigatória** a importação da tabela personalizada definida no arquivo:

- **Arquivo:** `Table Artefatos.xml`  
- **Tipo:** XML (definição de tabela / Update Set)

Essa tabela é responsável por:

- Centralizar o mapeamento dos tipos de artefatos  
- Armazenar nomes amigáveis, descrições e classificações  
- Apoiar a tradução técnica → funcional (**Dev → PO**)  
- Garantir padronização e consistência da documentação  

📌 **Sem a importação dessa tabela, a solução pode:**

- Não reconhecer corretamente os tipos de artefatos  
- Gerar documentação incompleta  
- Falhar na tradução de nomes e descrições  

---

## 🛠️ Como Usar  
1. Abra a UI Page  
2. Digite o nome do Update Set  
3. Escolha o público (Dev / PO)  
4. Clique em **⚙️ Gerar Documentação**  
5. (Opcional) Adicione imagens e descrições  
6. Clique em **💾 Exportar PDF**

---

## 📌 Requisitos  
- Permissão para ler **sys_update_xml**  
- Acesso às tabelas relacionadas a artefatos  
- Navegador moderno  
- Script Include client‑callable habilitado  

---

## 🎯 Benefícios  
- Padroniza documentação técnica  
- Melhora governança e auditoria  
- Facilita comunicação entre dev, QA e negócio  
- Aumenta velocidade de entrega  
- Centraliza informações em um único lugar  
- Elimina documentação manual e repetitiva  

---

## 👤 Autor  
**Matheus Avelar**  
Desenvolvedor ServiceNow & Web Developer  
🔗 [LinkedIn](https://www.linkedin.com/in/matheusavelar/)

---

## 📄 Licença  
Projeto open‑source, adaptável para outras instâncias ServiceNow.

