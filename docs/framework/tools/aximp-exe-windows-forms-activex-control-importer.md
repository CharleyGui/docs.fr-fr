---
title: Aximp.exe (Windows Forms ActiveX Control Importer)
description: Comprendre Aximp.exe, l’importateur de contrôles ActiveX Windows Forms. Cet outil convertit les définitions de type dans une bibliothèque de types COM pour ActiveX en Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
ms.openlocfilehash: 97e5201aecc540594aa154bb5a2e93e85c925570
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247341"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Windows Forms ActiveX Control Importer)

L'importateur de contrôles ActiveX convertit les définitions de types d'une bibliothèque de types COM associées à un contrôle ActiveX en un contrôle Windows Forms.  
  
 Windows Forms peut héberger uniquement des contrôles Windows Forms, c'est-à-dire, des classes dérivées de <xref:System.Windows.Forms.Control>. Aximp.exe génère une classe wrapper associée à un contrôle ActiveX qui peut être hébergée dans un Windows Form. Cela vous permet d'utiliser la même prise en charge au moment du design et la même méthodologie de programmation que pour d'autres contrôles Windows Forms.  
  
 Pour héberger le contrôle ActiveX, vous devez générer un contrôle wrapper qui dérive de <xref:System.Windows.Forms.AxHost>. Ce contrôle wrapper contient une instance du contrôle ActiveX sous-jacent. Il sait comment communiquer avec le contrôle ActiveX, mais il se présente comme un contrôle Windows Forms. Le contrôle ainsi généré héberge le contrôle ActiveX dont il expose les propriétés, les méthodes et les événements comme si ces derniers lui appartenaient.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Notes  
  
|Argument|Description|  
|--------------|-----------------|  
|*file*|Nom du fichier source contenant le contrôle ActiveX à convertir. La valeur de cet argument doit présenter l'extension .dll ou .ocx.|  
  
|Option|Description|  
|------------|-----------------|  
|`/delaysign`|Spécifie à Aximp.exe que le contrôle résultant doit être signé à l'aide du processus de signature différée. Vous devez spécifier cette option avec l’option `/keycontainer:`, `/keyfile:` ou `/publickey:`. Pour plus d’informations sur le processus de signature différée, consultez [Temporisation de signature d’un assembly](../../standard/assembly/delay-sign.md).|  
|`/help`|Affiche la syntaxe et les options de commande de l'outil.|  
|`/keycontainer:`*containerName*|Signe le contrôle obtenu avec un nom fort en utilisant la paire de clés publique/privée présente dans le conteneur de clé spécifié par *nom_conteneur*.|  
|`/keyfile:`*nom du fichier*|Signe le contrôle résultant avec un nom fort en utilisant la paire de clés publique/privée officielle de l’éditeur présente dans *nom_fichier*.|  
|`/nologo`|Supprime l'affichage de la bannière de démarrage Microsoft.|  
|`/out:`*nom du fichier*|Spécifie le nom de l'assembly à créer.|  
|`/publickey:`*nom du fichier*|Signe le contrôle résultant avec un nom fort en utilisant la clé publique présente dans le fichier spécifié par *nom_fichier*.|  
|`/rcw:`*nom du fichier*|Utilise le wrapper RCW spécifié plutôt que d'en générer un nouveau. Vous pouvez spécifier plusieurs instances. Le répertoire actif est utilisé pour les chemins d’accès relatifs. Pour plus d’informations, consultez [Wrapper pouvant être appelé par le runtime](../../standard/native-interop/runtime-callable-wrapper.md).|  
|`/silent`|Supprime l'affichage des messages indiquant la réussite des opérations.|  
|`/source`|Génère le code source C# pour le wrapper Windows Forms.|  
|`/verbose`|Spécifie le mode Commentaires ; affiche des informations supplémentaires sur la progression de l'opération.|  
|`/?`|Affiche la syntaxe et les options de commande de l'outil.|  
  
 Aximp.exe convertit toute une bibliothèque de types de contrôles ActiveX à la fois et produit un ensemble d'assemblys contenant les métadonnées du Common Language Runtime et l'implémentation des contrôles pour les types définis dans la bibliothèque de types d'origines. Les fichiers générés sont nommés conformément à la règle suivante :  
  
 Proxy du Common Language Runtime pour les types COM : *progid*.dll  
  
 Proxy Windows Forms pour les contrôles ActiveX (où Ax est l’abréviation de ActiveX) : Ax *progid*.dll  
  
> [!NOTE]
> Si le nom d'un membre du contrôle ActiveX correspond à un nom défini dans le .NET Framework, Aximp.exe fait précéder le nom du membre avec « Ctl » lorsqu'il crée la classe dérivée AxHost. Par exemple, si votre contrôle ActiveX possède un membre nommé "Layout", il est renommé "CtlLayout" dans la classe dérivée AxHost, car l'événement Layout est défini dans le .NET Framework.  
  
 Vous pouvez examiner ces fichiers générés avec des outils comme [Ildasm.exe (Désassembleur IL)](ildasm-exe-il-disassembler.md).  
  
 L'utilisation d'Aximp.exe pour générer un assembly .NET pour le contrôle ActiveX WebBrowser (shdocvw.dll) n'est pas prise en charge.  
  
 L'exécution d'Aximp.exe sur shdocvw.dll créera toujours un autre fichier nommé shdocvw.dll dans le répertoire à partir duquel l'outil est exécuté. Si le fichier généré est placé dans le répertoire Documents and Settings, cela perturbe le fonctionnement de Microsoft Internet Explorer et de l'Explorateur Windows. Lorsque l'ordinateur est redémarré, Windows recherche une copie de shdocvw.dll dans le répertoire Documents and Settings avant de regarder dans le répertoire system32. Il utilise la copie trouvée dans Documents and Settings et essaie de charger les wrappers managés. Internet Explorer et l'Explorateur Windows ne fonctionnent pas correctement, car ils s'appuient sur le moteur de rendu figurant dans la version de shdocvw.dll qui se trouve dans le répertoire system32. Si ce problème survient, supprimez la copie de shdocvw.dll qui se trouve dans le répertoire Documents and Settings, puis redémarrez votre ordinateur.  
  
 L'utilisation d'Aximp.exe avec shdocvw.dll pour créer un assembly .NET en vue de son utilisation dans le développement d'une application peut également poser problème. Dans ce cas, votre application chargera la version système de shdocvw.dll ainsi que la version générée, et pourrait donner la priorité à la version système. Dans ce cas, lorsque vous essayez de charger une page web dans le contrôle webBrowser ActiveX, une boîte de dialogue Ouvrir/Enregistrer peut s’afficher. Si l’utilisateur clique sur **Ouvrir**, la page web s’ouvre dans Internet Explorer. Cela ne se produit que sur les ordinateurs exécutant Internet Explorer version 6 ou antérieure. Pour éviter ce problème, utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> managé ou Visual Studio pour générer le fichier shdocvw.dll managé, comme décrit dans [Guide pratique pour ajouter des références aux bibliothèques de types](../interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a> Exemple  

 La commande suivante génère MediaPlayer.dll et AxMediaPlayer.dll pour le contrôle Media Player `msdxm.ocx`.  
  
```console
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Ildasm.exe (Désassembleur IL)](ildasm-exe-il-disassembler.md)
