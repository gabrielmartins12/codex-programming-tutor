# Tutor de Programação para Codex

Uma skill para trabalhar em projetos de programação enquanto aprende. Ela orienta o Codex a explicar as mudanças em linguagem simples, fazer implementações pequenas e manter o trabalho visível no diretório do projeto.

Inclui ensino visual e aulas interativas em HTML com motion, diagramas, exemplos do projeto e prática com feedback. O player e as ferramentas de produção estão incluídos na própria skill; não é necessário instalar outra skill.

## O que a skill orienta o Codex a fazer

- Usar o idioma da conversa e considerar que a pessoa pode estar começando.
- Explicar o objetivo e os arquivos envolvidos antes de cada pequena implementação.
- Depois da mudança, explicar o que foi alterado, por que, como funciona e onde ajustar o comportamento.
- Trabalhar no diretório do projeto que a pessoa consegue acompanhar.
- Usar exemplos concretos para explicar termos e construções novas.
- Priorizar explicações visuais quando essa for a preferência da pessoa.
- Mostrar execução, caminho dos dados e mudanças de estado em aulas interativas, com Continuar, Voltar e replay.
- Conectar cada demonstração aos arquivos do projeto e a uma alteração que a pessoa pode experimentar.
- Usar motion para explicar mecanismos, com suporte a movimento reduzido e revisão das cenas.

## Instalar no Codex

Com o repositório público no GitHub, execute:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo gabrielmartins12/codex-programming-tutor \
  --path skills/programming-tutor \
  --name programming-tutor
```

A skill será instalada em `~/.codex/skills/programming-tutor`. Em outra conta ou computador, a pessoa precisa ter acesso ao repositório e instalar a skill no próprio Codex. Se o Codex já estiver aberto, comece uma nova conversa para ele descobrir a skill.

## Atualizar a instalação

Depois de atualizar o repositório, copie a pasta completa `skills/programming-tutor/` para `~/.codex/skills/programming-tutor/`, incluindo `references/` e `visual/`. Atualizar apenas `SKILL.md` deixa os recursos de aula ausentes. A cópia local do Codex não acompanha automaticamente as mudanças do GitHub.

## Usar

Depois da instalação, abra um projeto e peça ajuda para desenvolver enquanto aprende. A descrição da skill informa ao Codex quando ela é relevante; também é possível pedir explicitamente para usar a skill `programming-tutor`.

Exemplo: “Use programming-tutor. Aprendo melhor visualmente: mostre com uma aula interativa e animações como os dados deste formulário chegam ao banco, explicando os arquivos envolvidos.”

As aulas funcionam offline depois de empacotadas. Para produzir e revisar aulas, as ferramentas usam Node.js, Playwright, Sharp e um Chromium disponível. Essas dependências ficam em uma pasta de ferramentas, sem entrar no aplicativo desenvolvido. Áudio, PDF e vídeo não fazem parte do fluxo padrão.

## Origem dos recursos visuais

A base de aulas vem de [`aula-interativa`](https://github.com/gabrielgreco1/skills/tree/main/aula-interativa), de Gabriel Greco. Princípios selecionados de [`motion-designer`](https://github.com/gabrielgreco1/skills/tree/main/motion-designer) orientam clareza e continuidade das animações. Consulte [os créditos e a revisão de origem](skills/programming-tutor/visual/ATTRIBUTION.md).

## Arquivo principal

- [`skills/programming-tutor/SKILL.md`](skills/programming-tutor/SKILL.md): instruções que o Codex consulta para seguir o estilo de tutoria.

