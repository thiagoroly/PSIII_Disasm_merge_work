# PSIII Merge Plan

Projeto de mescla entre:

- Phantasy Star III English Translation v1.2
- Phantasy Star III General Improvement v1.2

A base técnica do projeto é a disassembly recompilável da versão UE de Phantasy Star III.

## Objetivo principal

Criar uma versão mesclada de Phantasy Star III que combine:

1. A retradução em inglês mais próxima do roteiro japonês.
2. Correções de bugs presentes na retradução.
3. Melhorias de gameplay, itens, lojas, baús, NPCs e apresentação do General Improvement.
4. Ajustes estéticos próprios quando necessário.

## Política geral da mescla

### Texto e lore

A retradução deve ser usada como principal referência para:

- roteiro principal;
- nomes de personagens;
- nomes de lugares;
- tom geral dos diálogos;
- coerência com o roteiro japonês.

O General Improvement pode contribuir com:

- novos NPCs;
- diálogos adicionais;
- textos explicativos;
- expansão de lore.

Quando houver conflito, os textos adicionais devem ser adaptados para combinar com a nomenclatura e estilo da retradução.

### Gameplay e conteúdo

O General Improvement deve ser usado como principal referência para:

- novos itens;
- remoção ou fusão de itens pouco úteis;
- lojas;
- baús;
- permissões de equipamento;
- equipamentos iniciais;
- melhorias de balanceamento;
- NPCs extras;
- casas vazias preenchidas.

### Bugfixes

Bugfixes devem ser avaliados individualmente.

Regra:

- se ambos os hacks corrigem o mesmo bug, escolher apenas uma implementação;
- evitar duplicar correções;
- preferir mudanças pequenas, documentadas e testáveis;
- cada bugfix deve entrar em commit próprio sempre que possível.

### Paletas e gráficos

As mudanças visuais dos hacks não devem ser aceitas automaticamente.

Política inicial:

- manter retratos próximos da arte original ou da intenção visual principal;
- ajustar sprites de cenário quando for mais coerente;
- evitar recolorir retratos apenas para combinar com sprites pequenos;
- usar Aridia como ferramenta auxiliar de inspeção/edição visual;
- implementar mudanças finais na disassembly, não diretamente na ROM final.

Caso específico já decidido:

- Lune, Luise e Luna: preferir manter os retratos e ajustar sprites/paletas de campo, se necessário.

## Fonte oficial

A fonte oficial da ROM mesclada é o código ASM neste repositório.

Arquivos ROM gerados, como `ps3built.bin`, não devem ser versionados.

## Ordem inicial de trabalho

1. Validar disassembly limpa.
2. Aplicar bugfixes pequenos e isolados.
3. Portar correções de bugs da retradução.
4. Comparar tabelas de itens/equipamentos.
5. Portar melhorias de lojas e baús.
6. Portar NPCs e diálogos adicionais.
7. Revisar paletas e gráficos.
8. Testar rotas e saves.
9. Gerar patch final.
