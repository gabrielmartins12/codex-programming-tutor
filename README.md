# Tutor de Programação para Codex

Uma skill para trabalhar em projetos de programação enquanto aprende. Ela orienta o Codex a explicar as mudanças em linguagem simples, fazer implementações pequenas e manter o trabalho visível no diretório do projeto.

## O que a skill orienta o Codex a fazer

- Usar o idioma da conversa e considerar que a pessoa pode estar começando.
- Explicar o objetivo e os arquivos envolvidos antes de cada pequena implementação.
- Depois da mudança, explicar o que foi alterado, por que, como funciona e onde ajustar o comportamento.
- Trabalhar no diretório do projeto que a pessoa consegue acompanhar.
- Usar exemplos concretos para explicar termos e construções novas.

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

Depois de atualizar o repositório, atualize também a cópia instalada em `~/.codex/skills/programming-tutor/SKILL.md`. A cópia local do Codex não acompanha automaticamente as mudanças do GitHub.

## Usar

Depois da instalação, abra um projeto e peça ajuda para desenvolver enquanto aprende. A descrição da skill informa ao Codex quando ela é relevante; também é possível pedir explicitamente para usar a skill `programming-tutor`.

## Arquivo principal

- [`skills/programming-tutor/SKILL.md`](skills/programming-tutor/SKILL.md): instruções que o Codex consulta para seguir o estilo de tutoria.

