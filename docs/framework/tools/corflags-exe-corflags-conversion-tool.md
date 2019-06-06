---
title: CorFlags.exe (outil de conversion CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef10ba566842db26ed8c29643535c41aaca9806
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378661"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (outil de conversion CorFlags)
L’outil de conversion CorFlags vous permet de configurer la section CorFlags de l’en-tête d’une image exécutable portable.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre requis|Description|  
|------------------------|-----------------|  
|`assembly`|Nom de l'assembly pour lequel CorFlags doit être configuré.|  
  
|Option|Description|  
|------------|-----------------|  
|**/32BIT[REQ]+**|Définit l'indicateur 32BITREQUIRED.|  
|**/32BIT[REQ]-**|Efface l'indicateur 32BITREQUIRED.|  
|**/32BITPREF+**|Définit l'indicateur 32BITPREFERRED. L'application s'exécute comme un processus 32 bits même sur les plateformes 64 bits. Affectez cet indicateur uniquement sur les fichiers EXE. Si l'indicateur est défini sur une DLL, la DLL ne charge pas dans les processus 64 bits, et une exception <xref:System.BadImageFormatException> est levée. Un fichier EXE avec cet indicateur peut être chargé dans un processus 64 bits.<br /><br /> Nouveautés de .NET Framework 4.5.|  
|**/32BITPREF-**|Efface l'indicateur 32BITPREFERRED.<br /><br /> Nouveautés de .NET Framework 4.5.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
|**/Force**|Force une mise à jour même si l'assembly est associé à un nom fort. **Important :**  si vous mettez à jour un assembly à nom fort, vous devez le signer à nouveau avant d’exécuter son code.|  
|**/help**|Affiche la syntaxe et les options de commande de l'outil.|  
|**/ILONLY+**|Définit l'indicateur ILONLY.|  
|**/ILONLY-**|Efface l'indicateur ILONLY.|  
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|  
|**/RevertCLRHeader**|Rétablit l'en-tête du CLR à la version 2.0.|  
|**/UpgradeCLRHeader**|Met à niveau l'en-tête du CLR à la version 2.5. **Remarque :**  les assemblys doivent avoir la version 2.5 ou une version ultérieure de l’en-tête du CLR pour s’exécuter en mode natif.|  
  
## <a name="remarks"></a>Remarques  
 Si aucune option n'est spécifiée, l'outil de conversion CorFlags affiche les indicateurs pour l'assembly spécifié.  
  
## <a name="see-also"></a>Voir aussi

- [Outils](../../../docs/framework/tools/index.md)
- [Applications 64 bits](../../../docs/framework/64-bit-apps.md)
- [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
