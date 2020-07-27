---
title: Lc.exe (License Compiler)
description: Utilisez Lc.exe, le compilateur de licences. Cet outil lit les fichiers texte qui contiennent des informations de licence et crée un fichier binaire à incorporer dans un exécutable CLR en tant que ressource.
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 45a80ba7c3e24c0f419758315b2d2daafd3890f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164249"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (License Compiler)
L'outil License Compiler lit les fichiers texte comportant des informations sur les licences et génère un fichier binaire pouvant être incorporé dans un exécutable du Common Language Runtime en tant que ressource.  
  
 Un fichier .licx est automatiquement généré ou mis à jour par le concepteur Windows Forms lorsqu'un contrôle sous licence est ajouté au formulaire. Dans le cadre de la compilation, le système de projet transforme le fichier texte .licx en ressource binaire .licenses qui assure la prise en charge des licences de contrôles .NET. La ressource binaire est ensuite incorporée dans la sortie de projet.  
  
 La compilation croisée entre 32 bits et 64 bits n'est pas prise en charge lorsque vous utilisez l'outil License Compiler lors de la génération de votre projet. Cela est dû au fait que l'outil License Compiler doit charger des assemblys et que le chargement d'assemblys 64 bits depuis une application 32 bits n'est pas autorisé, et vice versa. Dans ce cas, utilisez l'outil License Compiler à partir de la ligne de commande pour compiler la licence manuellement et spécifiez l'architecture correspondante.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Option|Description|  
|------------|-----------------|  
|**/complist:** *filename*|Spécifie le nom d'un fichier comportant la liste des composants sous licence à inclure dans le fichier .licenses. Chaque composant est référencé avec son nom complet (un seul composant par ligne).<br /><br /> Les utilisateurs de ligne de commande peuvent spécifier un fichier distinct pour chaque formulaire du projet. Lc.exe accepte plusieurs fichiers d'entrée et génère un seul fichier .licenses.|  
|**/h**[**IDE**]|Affiche la syntaxe et les options de commande de l'outil.|  
|**/i:** *module*|Spécifie les modules contenant les composants répertoriés dans le fichier **/complist**. Pour spécifier plusieurs modules, utilisez plusieurs indicateurs **/i**.|  
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|  
|**/outdir:** *path*|Spécifie le répertoire dans lequel placer le fichier .licenses de sortie.|  
|**/target:** *targetPE*|Spécifie l'exécutable pour lequel le fichier .licenses est en cours de génération.|  
|**/v**|Spécifie le mode détaillé ; affiche des informations sur la progression de la compilation.|  
|**@***fichier*|Spécifie le fichier de réponse (.rsp).|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="example"></a>Exemple  
  
1. Si vous utilisez un contrôle sous licence `MyCompany.Samples.LicControl1` contenu dans `Samples.DLL`, dans une application appelée `HostApp.exe`*, *vous pouvez créer le fichier `HostAppLic.txt` contenant ce qui suit.  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Créez le fichier .licenses appelé `HostApp.exe.licenses` à l'aide de la commande suivante.  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. Générez `HostApp.exe` y compris le fichier .licenses en tant que ressource. Si vous étiez en train de générer une application C#, vous utiliseriez alors la commande suivante pour générer votre application.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 La commande suivante compile `myApp.licenses` à partir des listes de composants sous licence spécifiées par `hostapplic.txt`, `hostapplic2.txt` et `hostapplic3.txt`. L'argument `modulesList` spécifie les modules qui comportent les composants sous licence.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Exemple de fichier de réponse  
 La liste suivante montre un exemple de fichier réponse, `response.rsp`. Pour plus d’informations sur les fichiers réponse, consultez [Fichiers réponse](/visualstudio/msbuild/msbuild-response-files).  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 La ligne de commande suivante utilise le fichier `response.rsp`.  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Al.exe (Assembly Linker)](al-exe-assembly-linker.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
