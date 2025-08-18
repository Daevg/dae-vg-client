# Instruções para Implementação do Botão WhatsApp

## ✅ Resumo da Implementação

Foi adicionado com sucesso um botão flutuante do WhatsApp no site DAE-VG. O botão está posicionado no canto inferior direito e direciona para o número **550800707444** com uma mensagem padrão em português.

## 📋 Alterações Realizadas

### 1. Novo Componente Criado
- **Arquivo**: `src/components/WhatsAppButton.tsx`
- **Funcionalidade**: Componente React que renderiza um botão flutuante verde com ícone do WhatsApp
- **Posicionamento**: Fixo no canto inferior direito (bottom-6 right-6)
- **Estilo**: Círculo verde (#25D366) com efeito hover e sombra

### 2. Integração no Layout Principal
- **Arquivo**: `src/app/layout.tsx`
- **Alteração**: Adicionado import e renderização do componente WhatsAppButton
- **Posição**: Após os componentes Control e VLibrasClient

### 3. Configuração do Número
- **Número**: 550800707444
- **Mensagem padrão**: "Olá! Gostaria de mais informações."
- **Comportamento**: Abre WhatsApp Web/App em nova aba

## 🧪 Testes Realizados

✅ **Teste Local Concluído**
- Servidor de desenvolvimento iniciado com sucesso
- Botão aparece corretamente no canto inferior direito
- Clique no botão redireciona para WhatsApp com número e mensagem corretos
- Design responsivo e não interfere no layout existente

## 📦 Branch de Desenvolvimento

- **Branch**: `feature/whatsapp-button`
- **Commit**: `e5a0b5c` - "feat: adicionar botão flutuante do WhatsApp"
- **Status**: Pronto para revisão e merge




## 🔍 Processo de Revisão e Aprovação

### Passo 1: Revisar as Alterações
```bash
# Visualizar as alterações na branch
git checkout feature/whatsapp-button
git diff main..feature/whatsapp-button

# Verificar arquivos modificados
git show --name-only e5a0b5c
```

### Passo 2: Testar Localmente
```bash
# Instalar dependências (se necessário)
yarn install

# Iniciar servidor de desenvolvimento
yarn dev

# Acessar http://localhost:3000/test-page para testar o botão
```

### Passo 3: Verificar Funcionalidades
- [ ] Botão aparece no canto inferior direito
- [ ] Botão tem cor verde (#25D366) e ícone do WhatsApp
- [ ] Clique abre WhatsApp com número 550800707444
- [ ] Mensagem padrão "Olá! Gostaria de mais informações." aparece
- [ ] Botão não interfere no layout existente
- [ ] Botão funciona em diferentes páginas do site

### Passo 4: Aprovação para Produção
Após a revisão e testes, se tudo estiver funcionando corretamente:

```bash
# Fazer merge da branch para main
git checkout main
git merge feature/whatsapp-button

# Fazer push para o repositório
git push origin main
```


## 🚀 Deploy em Produção

### Método 1: Deploy via Docker (Recomendado)
```bash
# No servidor de produção (177.200.190.14)
cd /caminho/do/projeto
git pull origin main

# Rebuild do container Docker
docker build -t nextjs-app .
docker stop nextjs
docker rm nextjs
docker run -d --name nextjs -p 3000:3000 nextjs-app
```

### Método 2: Deploy Manual
```bash
# No servidor de produção
git pull origin main
yarn install
yarn build
yarn start
```

### Verificação Pós-Deploy
1. Acesse https://daevg.com.br
2. Verifique se o botão do WhatsApp aparece no canto inferior direito
3. Teste o clique no botão para confirmar redirecionamento
4. Verifique em diferentes páginas do site

## ⚠️ Monitoramento
- Monitore logs do servidor após o deploy
- Verifique se não há erros de JavaScript no console do navegador
- Confirme que o site continua funcionando normalmente


## 🔄 Procedimentos de Rollback

### Rollback Rápido (Emergência)
Se houver problemas críticos após o deploy:

```bash
# Voltar para o commit anterior ao botão do WhatsApp
git checkout main
git reset --hard HEAD~1
git push --force origin main

# Rebuild e restart do container
docker build -t nextjs-app .
docker stop nextjs && docker rm nextjs
docker run -d --name nextjs -p 3000:3000 nextjs-app
```

### Rollback Seletivo (Remover apenas o botão)
Para remover apenas o botão do WhatsApp mantendo outras alterações:

```bash
# Criar branch para rollback
git checkout -b rollback/remove-whatsapp-button

# Reverter apenas os arquivos do WhatsApp
git checkout HEAD~1 -- src/components/WhatsAppButton.tsx
git checkout HEAD~1 -- src/app/layout.tsx

# Remover arquivo do componente
rm src/components/WhatsAppButton.tsx

# Commit e merge
git add .
git commit -m "rollback: remover botão do WhatsApp"
git checkout main
git merge rollback/remove-whatsapp-button
```

## 🛠️ Solução de Problemas

### Problema: Botão não aparece
**Possíveis causas:**
- Erro de build do Next.js
- Problema de CSS/Tailwind
- Erro de importação do componente

**Solução:**
```bash
# Verificar logs de build
yarn build

# Verificar console do navegador
# Inspecionar elemento para ver se o botão está sendo renderizado
```

### Problema: Botão não redireciona corretamente
**Possíveis causas:**
- Número de telefone incorreto
- Problema com encoding da mensagem

**Solução:**
- Verificar se o número 550800707444 está correto
- Testar URL manualmente: `https://wa.me/550800707444?text=Olá!%20Gostaria%20de%20mais%20informações.`

### Problema: Botão interfere no layout
**Possíveis causas:**
- Conflito com z-index de outros elementos
- Problema de posicionamento CSS

**Solução:**
- Ajustar z-index no componente WhatsAppButton.tsx
- Modificar posicionamento (bottom/right values)


## 🎨 Personalização Futura

### Alterar Número do WhatsApp
Para alterar o número de telefone:
1. Edite o arquivo `src/components/WhatsAppButton.tsx`
2. Modifique a linha: `const phoneNumber = '550800707444';`
3. Substitua pelo novo número (formato: código do país + DDD + número)

### Alterar Mensagem Padrão
Para alterar a mensagem padrão:
1. Edite o arquivo `src/components/WhatsAppButton.tsx`
2. Modifique a linha: `const message = 'Olá! Gostaria de mais informações.';`
3. Substitua pela nova mensagem desejada

### Alterar Posição do Botão
Para alterar a posição do botão:
1. Edite o arquivo `src/components/WhatsAppButton.tsx`
2. Modifique as classes CSS: `bottom-6 right-6`
3. Opções: `top-6`, `bottom-6`, `left-6`, `right-6`

### Alterar Aparência do Botão
Para alterar cores, tamanho ou ícone:
1. Edite o arquivo `src/components/WhatsAppButton.tsx`
2. Modifique as propriedades de style:
   - `backgroundColor`: cor de fundo
   - `width`/`height`: tamanho do botão
   - SVG path: ícone do WhatsApp

## 📞 Contatos e Suporte

### Informações Técnicas
- **Repositório**: https://github.com/daevgsites/dae-vg-client
- **Branch**: feature/whatsapp-button
- **Tecnologia**: Next.js 14.2.4 + TypeScript + Tailwind CSS

### Backup de Segurança
- Backup completo do código foi criado na branch `feature/whatsapp-button`
- Estado original preservado na branch `main` (antes do merge)
- Todas as alterações estão versionadas no Git

---

## ✅ Checklist Final

Antes de considerar a implementação concluída:

- [ ] Código revisado e aprovado
- [ ] Testes locais realizados com sucesso
- [ ] Deploy em produção executado
- [ ] Verificação pós-deploy realizada
- [ ] Botão funcionando corretamente no site live
- [ ] Documentação entregue e compreendida
- [ ] Procedimentos de rollback testados (opcional)

**Data da Implementação**: 18 de Agosto de 2025  
**Desenvolvedor**: Manus AI Assistant  
**Status**: ✅ Implementação Concluída - Aguardando Deploy

