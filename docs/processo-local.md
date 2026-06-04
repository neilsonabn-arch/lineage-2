# Processo Local Inicial

## Pasta oficial do projeto

Use como pasta principal:

```powershell
C:\Users\AbysPC\Documents\GitHub\lineage-2-repo
```

## Atualizar repositório

```powershell
cd "C:\Users\AbysPC\Documents\GitHub\lineage-2-repo"
git pull origin main
```

## Atualizar submodules

```powershell
git submodule update --init --recursive
```

## Verificar status

```powershell
git status
```

O ideal é aparecer:

```txt
nothing to commit, working tree clean
```

## Base Classic

A base Classic está registrada como submodule:

```txt
L2J_Mobius_Classic_2.9.5_Saviors-base
```

Para entrar nela:

```powershell
cd "C:\Users\AbysPC\Documents\GitHub\lineage-2-repo\L2J_Mobius_Classic_2.9.5_Saviors-base"
```

## Primeira auditoria local da base

Procurar arquivos de banco:

```powershell
Get-ChildItem -Recurse -File -Include *.sql,*.bat,*.sh | Select-Object FullName
```

Procurar configurações de LoginServer/GameServer:

```powershell
Get-ChildItem -Recurse -File -Include *.ini,*.properties,*.xml | Select-String -Pattern "loginserver","gameserver","jdbc","database","mysql","mariadb" | Select-Object Path,LineNumber,Line -First 100
```

Procurar versão Java/build:

```powershell
Get-ChildItem -Recurse -File -Include pom.xml,build.gradle,*.bat,*.sh | Select-String -Pattern "java","javac","maven","gradle","ant" | Select-Object Path,LineNumber,Line -First 100
```

## Próximo objetivo

Antes de programar a Prime War, precisamos confirmar:

- Como compilar a base
- Como instalar o banco
- Como iniciar LoginServer
- Como iniciar GameServer
- Onde scripts customizados devem ser colocados
