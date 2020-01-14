---
title: SecAnnotate.exe (outil .NET Security Annotator)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: ffc275c588775fb79da276be904ada90a5a31bad
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937926"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (outil .NET Security Annotator)
L'outil .NET Security Annotator (SecAnnotate.exe) est une application en ligne de commande qui identifie les parties `SecurityCritical` et `SecuritySafeCritical` d'un ou de plusieurs assemblys.  
  
 Une extension Visual Studio, [Security Annotator](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator), fournit une interface utilisateur graphique à SecAnnotate.exe et vous permet d’exécuter l’outil à partir de Visual Studio.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l’invite de commandes, tapez la ligne suivante, où les *paramètres* sont décrits dans la section suivante et où les *assemblys* se composent d’un ou de plusieurs noms d’assembly séparés par des espaces :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parameters  
  
|Option|Description|  
|------------|-----------------|  
|`/a`<br /><br /> ou<br /><br /> `/showstatistics`|Affiche des statistiques relatives à l'utilisation de la transparence dans les assemblys analysés.|  
|*répertoire* `/d:`<br /><br /> ou<br /><br /> *répertoire* `/referencedir:`|Spécifie un répertoire dans lequel les assemblys dépendants doivent être recherchés lors de l'annotation.|  
|`/i`<br /><br /> ou<br /><br /> `/includesignatures`|Inclut les informations de signature étendue dans le fichier de rapport d'annotation.|  
|`/n`<br /><br /> ou<br /><br /> `/nogac`|Supprime la recherche d'assemblys référencés dans le Global Assembly Cache.|  
|`/o:` *Output. xml*<br /><br /> ou<br /><br /> `/out:` *Output. xml*|Spécifie le fichier d'annotation de sortie.|  
|`/p:` *maxpasses*<br /><br /> ou<br /><br /> `/maximumpasses:` *maxpasses*|Spécifie le nombre maximal de passes d'annotation à effectuer avant d'arrêter la génération de nouvelles annotations.|  
|`/q`<br /><br /> ou<br /><br /> `/quiet`|Spécifie le mode silencieux, dans lequel l'annotateur ne génère pas de messages d'état, mais uniquement des informations sur les erreurs.|  
|*assembly* `/r:`<br /><br /> ou<br /><br /> *assembly* `/referenceassembly:`|Inclut l'assembly spécifié lors de la résolution d'assemblys dépendants pendant l'annotation. Les assemblys de référence ont la priorité sur les assemblys figurant dans le chemin d’accès de référence.|  
|`/s:` *RuleName*<br /><br /> ou<br /><br /> `/suppressrule:` *RuleName*|Supprime l'exécution de la règle de transparence spécifiée sur les assemblys d'entrée.|  
|`/t`<br /><br /> ou<br /><br /> `/forcetransparent`|Force l'outil Annotator à traiter tous les assemblys qui n'ont pas d'annotations de transparence comme s'ils étaient entièrement transparents.|  
|`/t`:*assembly*<br /><br /> ou<br /><br /> `/forcetransparent`:*assembly*|Forcer l'assembly donné à être transparent, quelles que soient ses annotations actuelles au niveau de l'assembly.|  
|||  
|`/v`<br /><br /> ou<br /><br /> `/verify`|Vérifie uniquement que des annotations d'assembly sont correctes ; n'essaie pas d'exécuter plusieurs passages pour rechercher toutes les annotations obligatoires si l'assembly ne vérifie pas.|  
|`/x`<br /><br /> ou<br /><br /> `/verbose`|Spécifie la sortie des commentaires lors de l'annotation.|  
|*répertoire* `/y:`<br /><br /> ou<br /><br /> *répertoire* `/symbolpath:`|Inclut le répertoire spécifié lors de la recherche de fichiers de symboles pendant l'annotation.|  
  
## <a name="remarks"></a>Notes  
 Les paramètres et assemblys peuvent également être fournis dans un fichier réponse qui est spécifié sur la ligne de commande et est préfixé avec un arobase (@). Chaque ligne dans le fichier réponse doit contenir un paramètre unique ou nom de l'assembly.  
  
 Pour plus d’informations sur .NET Security Annotator, consultez l’entrée [Utilisation de SecAnnotate pour analyser vos assemblys pour les violations de transparence](https://docs.microsoft.com/archive/blogs/shawnfa/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example) dans le blog de sécurité .NET.  
  
## <a name="examples"></a>Exemples
