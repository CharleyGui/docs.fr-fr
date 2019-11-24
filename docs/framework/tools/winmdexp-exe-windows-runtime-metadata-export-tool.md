---
title: Winmdexp.exe (outil d'exportation de métadonnées Windows Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
ms.openlocfilehash: 52820b78f6ed7b02e80df66f90a01143b31d9b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447281"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (outil d'exportation de métadonnées Windows Runtime)
L'outil Metadata Export Windows Runtime (Winmdexp.exe) transforme un module .NET Framework en un fichier qui contient des métadonnées Windows Runtime. Bien que les assemblys .NET Framework et les fichiers de métadonnées Windows Runtime utilisent le même format physique, il y a des différences dans le contenu des tables de métadonnées. Autrement dit, les assemblys .NET Framework ne sont pas utilisables automatiquement comme composants Windows Runtime. Le processus qui transforme un module .NET Framework en composant Windows Runtime s’appelle *exportation*. Dans .NET Framework 4.5 et .NET Framework 4.5.1, le fichier de métadonnées Windows (.winmd) résultant contient à la fois les métadonnées et l’implémentation.  
  
 Quand vous utilisez le modèle **Composant Windows Runtime**, qui se trouve dans le **Windows Store** pour C# et Visual Basic dans Visual Studio 2013 ou Visual Studio 2012, la cible du compilateur est un fichier .winmdobj et une étape de génération appelle Winmdexp.exe pour exporter le fichier .winmdobj vers un fichier .winmd. C'est la méthode recommandée pour générer un composant Windows Runtime. Utilisez Winmdexp.exe directement lorsque vous voulez contrôler davantage le processus de génération que Visual Studio le permet.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Argument ou option|Description|  
|------------------------|-----------------|  
|`winmdmodule`|Spécifie le module (.winmdobj) à exporter. Un seul module est autorisé. Pour créer ce module, utilisez l'option de compilateur `/target` avec la cible `winmdobj`. See [-target:winmdobj (C# Compiler Options)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) or [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Spécifie le fichier de documentation XML de sortie que Winmdexp.exe produira. Dans .NET Framework 4.5, le fichier de sortie est essentiellement identique au fichier de documentation XML d’entrée.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Spécifie le nom du fichier de documentation XML que le compilateur a produit avec `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Indique le nom du fichier de la base de données du programme (PDB) qui contient les symboles pour `winmdmodule`.|  
|`/nowarn:` `warning`|Supprime le nombre d'avertissements indiqué. Pour *warning*, fournissez uniquement la partie numérique du code d'erreur, sans zéro significatif.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Indique le nom du fichier de métadonnées Windows (.winmd) de sortie.|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Spécifie le nom du fichier de la base de données du programme (PDB) de sortie qui contiendra les symboles pour le fichier de métadonnées Windows (.winmd) exporté.|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Indique un fichier de métadonnées (.winmd ou assembly) à référencer lors de l'exportation. Si vous utilisez les assemblys de référence dans « \Program files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5 » (« \Program Files\\... » sur les ordinateurs 32 bits), incluez les références à System.Runtime.dll et mscorlib.dll.|  
|`/utf8output`|Spécifie que les messages de sortie utilisent un encodage en UTF-8.|  
|`/warnaserror+`|Spécifie que tous les avertissements doivent être traités comme des erreurs.|  
|**@** `responsefile`|Spécifie un fichier de réponse (.rsp) qui contient des options (et éventuellement `winmdmodule`). Chaque ligne dans `responsefile` doit contenir un seul argument ou une seule option.|  
  
## <a name="remarks"></a>Notes  
 Winmdexp.exe n'est pas conçu pour convertir un assembly. NET Framework arbitraire en un fichier .winmd. Il requiert un module compilé avec l'option `/target:winmdobj`, et des restrictions supplémentaires s'appliquent. La plus importante de ces restrictions est que tous les types qui sont exposés dans la surface API de l'assembly doivent être de type Windows Runtime. For more information, see the "Declaring types in Windows Runtime Components" section of the article [Creating Windows Runtime Components in C# and Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110)).
  
 When you write a Windows 8.x Store app or a Windows Runtime component with C# or Visual Basic, the .NET Framework provides support to make programming with the Windows Runtime more natural. Ce sujet est abordé dans l’article [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). Dans le processus, certains types de Windows Runtime utilisés couramment sont mappés en types .NET Framework. Winmdexp.exe inverse ce processus et produit une surface API qui utilise les types Windows Runtime correspondants. For example, types that are constructed from the <xref:System.Collections.Generic.IList%601> interface map to types that are constructed from the Windows Runtime <xref:Windows.Foundation.Collections.IVector%601> interface.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Création de composants Windows Runtime en C# et Visual Basic](https://docs.microsoft.com/previous-versions/br230301(v=vs.110))
- [Messages d’erreur Winmdexp.exe](winmdexp-exe-error-messages.md)
- [Outils de génération, de déploiement et de configuration (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
