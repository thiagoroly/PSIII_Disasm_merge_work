# PSIII Merge Changelog

Este arquivo documenta as alterações feitas no projeto de mescla.

O objetivo é registrar não apenas o que foi alterado, mas também por que a alteração foi feita.

## Formato

Cada entrada deve conter:

- Status
- Categoria
- Local no código
- Origem da alteração
- Descrição
- Motivo
- Teste recomendado

---

## Alterações aplicadas

### 001 - Corrigir uso indevido de equipamentos fora de batalha

**Status:** aplicado

**Categoria:** bugfix / menu / itens

**Local:**

- `ps3.asm`
- rotina `MenuItem_ActionUse`

**Alteração:**

```asm
cmpi.b  #ItemID_ShortSwd, d7
```

foi alterado para:

```asm
cmpi.w  #ItemID_ShortSwd, d7
```

**Origem:**

- Comentário existente na própria disassembly.
- Também relacionado aos bugfixes presentes na retradução.

**Motivo:**

A comparação byte-sized permitia que certos equipamentos com efeitos de técnica fossem usados fora de batalha de forma indevida.

**Teste recomendado:**

- Abrir o menu de itens.
- Confirmar que itens consumíveis normais ainda funcionam.
- Confirmar que equipamentos com efeitos especiais não podem ser abusados fora de batalha.
- Confirmar que o jogo não trava ao abrir o menu de itens.

---

### 002 - Corrigir inicialização do objeto do submersível no mundo de Laya

**Status:** aplicado

**Categoria:** bugfix / objeto / mapa

**Local:**

- `ps3.asm`
- rotina `Obj_LayaWorldSubmersible`

**Alteração:**

```asm
move.b  #1, $E(a6)
```

foi alterado para:

```asm
move.b  #1, $E(a5)
```

**Origem:**

- Comentário existente na própria disassembly.

**Motivo:**

A rotina estava escrevendo em `a6`, mas o objeto atual usa `a5`. A correção faz a inicialização agir sobre o objeto correto.

**Teste recomendado:**

- Iniciar a ROM e confirmar boot normal.
- Testar progressão até o uso/visualização do submersível no mundo de Laya.
- Confirmar que o mapa não apresenta comportamento anormal relacionado ao objeto.

---

### 003 - Corrigir Pron Glitch na conversão das armas Nei

**Status:** aplicado

**Categoria:** bugfix / inventário / evento final

**Local:**

- `ps3.asm`
- rotina `ConvertLegendToNeiWpns`

**Alteração:**

A rotina agora verifica se o personagem possui `0` itens antes de tentar percorrer o inventário.

Foi adicionada uma ramificação para pular diretamente para o próximo personagem quando o inventário está vazio.

**Origem:**

- Comentário existente na própria disassembly.
- Bugfix também listado na retradução.

**Motivo:**

A rotina original subtraía do contador de itens mesmo quando o personagem tinha inventário vazio. Isso podia fazer o loop acessar regiões erradas da RAM e sobrescrever dados indevidos.

Esse problema é conhecido como **Pron Glitch**.

**Teste recomendado:**

- Confirmar que a ROM inicia normalmente.
- Confirmar que New Game funciona.
- Confirmar que o menu abre.
- Teste completo pendente com save avançado próximo da conversão das armas lendárias em armas Nei.

---

## Alterações planejadas

### Bugfixes a avaliar

- Poison bug.
- Personagens mortos usando técnicas ou itens fora de batalha.
- Escapipe bug.
- Glitch da Lena presa.
- Verificação das armas lendárias.
- Pron glitch.
- Carryover de itens de Mieu e Wren.
- MysteryStar duplicada no inventário inicial de Luin.
- Sprite/animação de Luise.
- Tabela de experiência de Warrior Luna.
- Tabelas de técnicas de Laia/Gwyn e Warrior Luna.
- Shuttle SFX em Luin quest.
- Rebel Cave após recrutar Dan.
- Transfer de Cille para Kein/Ain.

### General Improvement a portar depois

- Novos itens.
- Alterações de lojas.
- Alterações de baús.
- Permissões de equipamento.
- Equipamentos iniciais.
- NPCs extras.
- Diálogos adicionais.
- Casas vazias preenchidas.
- Ajustes de mapas.
- Ajustes de paletas e sprites.

### Decisões estéticas pendentes

- Lune: manter retrato ou sprite como referência?
- Luise: manter retrato ou sprite como referência?
- Luna: manter retrato ou sprite como referência?
- Decidir quais recolors da retradução serão mantidos.
- Decidir quais recolors do General Improvement serão mantidos.
