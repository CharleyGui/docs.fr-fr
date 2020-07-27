---
title: Clrver.exe (outil CLR Version)
description: Passez en revue Clrver.exe, l’outil CLR version. Cet outil signale toutes les versions installées du common language runtime (CLR) sur l’ordinateur.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: e914034819418df00438c454e209e6c86779ba3c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167281"
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (outil CLR Version)
L'outil de version CLR (Clrver.exe) rapporte toutes les versions installées du CLR (Common Runtime Language) sur l'ordinateur.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a>Options  
  
|Option|Description|  
|------------|-----------------|  
|`-all`|Affiche tous les processus de l'ordinateur qui utilisent le CLR.|  
|*ELECTRIQUE*|Affiche la ou les versions du CLR utilisé par le processus qui a l'ID de processus spécifié (PID).|  
|`-?`|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Notes  
 Si vous appelez Clrver.exe sans option, il affiche toutes les versions de CLR installées. Si vous spécifiez PID pour un autre utilisateur, vous devez disposer des autorisations d'administrateur pour obtenir les informations de version.  
  
> [!NOTE]
> Dans Windows Vista et version ultérieure, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur. Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur. Par défaut, vous êtes dans le rôle d'utilisateur standard. Pour exécuter le code qui requiert une autorisation d'administration, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur. Cela peut être effectué au démarrage de l'invite de commandes en cliquant avec le bouton droit sur l'icône de l'invite de commandes et en indiquant que vous voulez l'exécuter en tant qu'administrateur.  
  
 La tentative afin de déterminer la version du CLR pour des processus SYSTÈME, SERVICE LOCAL et SERVICE RÉSEAU entraîne un message indiquant que le PID n'existe pas.  
  
## <a name="examples"></a>Exemples  
 La commande suivante affiche toutes les versions du CLR installée sur l'ordinateur.  
  
 `clrver`  
  
 La commande suivante affiche la version du CLR utilisée par le processus 128.  
  
 `clrver 128`  
  
 La commande suivante affiche tous les processus gérés et la version du CLR qu'ils utilisent.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
