# 📘 Update Set Documentation Hub (USDH)  
## Documentação automatizada, inteligente e integrada para Update Sets no ServiceNow.

O **Update Set Documentation Hub (USDH)** é uma solução completa desenvolvida para gerar documentação técnica e funcional de Update Sets de forma automática no ServiceNow.  
Ele unifica artefatos, evidências visuais, Instance Scan, descrições e links diretos em uma única visão clara, organizada e pronta para exportação.

Ideal para **desenvolvedores**, **QAs**, **arquitetos**, **POs** e **equipes de governança**, reduzindo esforço manual e padronizando entregas.

---

## 🚀 Funcionalidades Principais

### 🔧 1. Geração Automática de Documentação  
- Script Include dedicado: **GetUpdateSetDocumentation**  
- Gera HTML completo com:
  - Lista de artefatos por tipo  
  - Nome amigável do item  
  - Descrição técnica  
  - Status (criação, atualização, exclusão)  
  - Link direto para o registro no ServiceNow  
  - Ícones por tipo (ou fallback seguro sem emojis)  
- Tradutor de tipos para linguagem amigável para POs  
- Título dinâmico baseado no cenário de teste

---

### 📄 2. UI Page Moderna e Intuitiva  
Inclui:  
- Campo para nome do Update Set  
- Seleção do público (Dev/PO)  
- Botão **⚙️ Gerar Documentação**  
- Botão **💾 Exportar PDF**  
- Botão **📎 Anexar Imagens**  
- Pré‑visualização de evidências  
- Inputs adicionais:
  - Projeto  
  - Squad  
  - Story  
  - Cenário  
  - Ambiente  
  - Observações

---

### 📸 3. Gerenciamento de Evidências  
- Upload de imagens (PNG, JPG, GIF)  
- Campo de descrição para cada imagem  
- Preview antes da exportação  
- Validação do tipo de arquivo  
- Área de anexos aparece apenas após gerar documentação

---

### 🧠 4. Integração com Instance Scan  
Incluído diretamente na documentação:  
- Scans relacionados ao Update Set  
- Status (complete / failed)  
- Findings detectados  
- Contagem total  
- Severidade por cor  
- Links diretos para o registro  
- Expansão / contração de detalhes

---

### 🗂️ 5. Tipos de Artefatos Suportados  
**Back‑end**  
🧠 Script Include  
⚙️ Business Rule  
🩹 Fix Script  
⏰ Scheduled Job  
🌊 Flow  
🔌 REST API  
🔄 Transform Map  
🔒 ACL  
...

**Front‑end**  
🌍 UI Page  
🎬 UI Action  
💻 Client Script  
🏷️ Field Label  
🧱 Widget  
📊 Dashboard  
...

**Integrações**  
📡 REST Message  
🧴 SOAP Message  
🔗 IntegrationHub & Spokes  

**Outros**  
📦 Update Set  
🧭 System Property  
🎨 Style Sheet  
✉️ Email Template  
📘 Knowledge Article  
⏱️ SLA  
📈 Report  
...

---

## ⚙️ Arquitetura Técnica

### 🧩 Script Include – GetUpdateSetDocumentation  
**Métodos principais**  
| Método                     | Função                                                   |
|---------------------------|----------------------------------------------------------|
| `getDocumentation()`      | Gera o HTML completo da documentação                      |
| `getDescriptionByType()`  | Retorna descrição do item                                 |
| `getFriendlyName()`       | Formata nome amigável                                    |
| `getIconByType()`         | Retorna ícone/emoji/SVG do tipo                           |
| `getTranslatedTypeName()` | Tradução para perfil PO                                    |
| `getRecordLink()`         | Link direto para o registro                               |

---

### 🎨 UI Page  
- Jelly + Client Script  
- Design moderno e responsivo  
- Preview do conteúdo  
- Botão para exportar PDF  
- Validação e alertas amigáveis  

---

## ⚠️ Observações Importantes  
### ❗ Possível problema com emojis como ícones  
Ambientes podem ter:
- Erros de codificação UTF‑8  
- HTML quebrado  
- GlideAjax retornando vazio  
- Instâncias mais antigas com incompatibilidade  

### ✔️ Soluções recomendadas  
- Ativar **fallback sem emojis**  
- Usar SVG inline  
- `try/catch` no método de ícones  
- Flag: `useIcons = false`

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

