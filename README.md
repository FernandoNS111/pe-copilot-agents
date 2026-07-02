# PE Copilot Agents - GEN2 Power Electronics

Repositorio colaborativo de agentes de GitHub Copilot para soporte tecnico, diagnostico y operaciones de cargadores GEN2.

## Repo oficial

- URL web: https://github.com/FernandoNS111/pe-copilot-agents
- URL git: https://github.com/FernandoNS111/pe-copilot-agents.git

## Estructura del repositorio

```text
.github/
	agents/
		AgenteSCO-pro.agent.md
		AnalizadorOCPP.agent.md
		APIpoweronsupport.agent.md
		AsistenciaCargadores.agent.md
		CRON_monitoriza.agent.md
		dispersionparametros.agent.md
		enforce-auth-analyzer.agent.md
		Extraeparametrizaciones.agent.md
		MassiveJSON.agent.md
		ModbusWriter.agent.md
		monitoriza_v1.agent.md
		party-orchestrator.agent.md
		PUSH_PULL_agentes.agent.md
		ReparaHMI.agent.md
		ResumenticketingPONS.agent.md
		secureboot-agent.agent.md
```

## Requisitos para cada companero

1. VS Code instalado.
2. Extension GitHub Copilot instalada y activa.
3. Git instalado.
4. Acceso al repositorio en GitHub.
5. Permisos de escritura para push directo o uso de ramas/PR.

## Instalacion de agentes en VS Code (Windows)

1. Clonar el repositorio:

```powershell
git clone https://github.com/FernandoNS111/pe-copilot-agents.git
cd pe-copilot-agents
```

2. Copiar agentes al perfil local de Copilot:

```powershell
$dest = "$HOME\.copilot\agents"
New-Item -ItemType Directory -Force -Path $dest | Out-Null
Copy-Item ".github\agents\*.agent.md" $dest -Force
```

3. Recargar VS Code:

- Command Palette -> Developer: Reload Window

4. Verificar en Copilot Chat:

- Escribir `@` y confirmar que aparecen los agentes.

## Actualizacion rapida diaria (pull + sync local)

```powershell
cd pe-copilot-agents
git pull origin main
Copy-Item ".github\agents\*.agent.md" "$HOME\.copilot\agents" -Force
```

## Flujo colaborativo recomendado

### Opcion A: Rama y Pull Request (recomendado)

```powershell
cd pe-copilot-agents
git pull origin main
git checkout -b feat/nombre-cambio

# editar agentes/README

git add .github/agents README.md
git commit -m "feat: actualiza agentes"
git push origin feat/nombre-cambio
```

Despues abrir Pull Request a `main` en GitHub.

### Opcion B: Push directo a main (solo si el equipo lo permite)

```powershell
cd pe-copilot-agents
git pull origin main

# editar agentes/README

git add .github/agents README.md
git commit -m "chore: actualiza agentes"
git push origin main
```

## Convenciones del equipo

1. Un agente por archivo `.agent.md`.
2. Mantener `name`, `description` y `tools` consistentes en frontmatter.
3. Actualizar este README cuando se cree o cambie un agente.
4. No incluir secretos, tokens o contrasenas en agentes.
5. Validar duplicados entre `.github/agents` y `$HOME\.copilot\agents`.

## Script de instalacion para nuevos companeros

```powershell
$repo = "$HOME\pe-copilot-agents"
if (!(Test-Path $repo)) {
	git clone https://github.com/FernandoNS111/pe-copilot-agents.git $repo
}

Set-Location $repo
git pull origin main

$dest = "$HOME\.copilot\agents"
New-Item -ItemType Directory -Force -Path $dest | Out-Null
Copy-Item ".github\agents\*.agent.md" $dest -Force

Write-Host "Agentes instalados/actualizados. Recarga VS Code con: Developer: Reload Window"
```

## Agente para sincronizacion

- `PUSH_PULL_agentes` esta pensado para ayudar en tareas de sincronizacion (push/pull), comparacion local-remoto y mantenimiento del README.

