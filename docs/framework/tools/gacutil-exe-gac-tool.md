---
title: Gacutil.exe (outil Global Assembly Cache)
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
ms.openlocfilehash: 87f3cb799ba4e406906759e1facd19d00c8bdace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107498"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (outil Global Assembly Cache)

L'outil Global Assembly Cache vous permet d'afficher et de manipuler le contenu du Global Assembly Cache et du cache de téléchargement.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez :

## <a name="syntax"></a>Syntaxe

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Paramètres

|Argument|Description|
|--------------|-----------------|
|*Assemblyname*|Nom d'un assembly. Vous pouvez indiquer un nom d'assembly partiellement spécifié, tel que `myAssembly` ou un nom d'assembly complètement spécifié, tel que `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|
|*assemblyPath*|Nom d'un fichier comportant un manifeste d'assembly.|
|*assemblyListFile*|Chemin d’accès à un fichier texte ANSI qui répertorie des assemblys à installer ou à désinstaller. Pour utiliser un fichier texte afin d’installer des assemblys, spécifiez le chemin d’accès de chaque assembly sur une ligne distincte dans le fichier. L’outil interprète des chemins relatifs à l’emplacement de *assemblyListFile*. Pour utiliser un fichier texte afin de désinstaller des assemblys, indiquez le nom qualifié complet de chaque assembly sur une ligne distincte dans le fichier. Consultez les exemples de contenu de *assemblyListFile* plus loin dans cette rubrique.|

|Option|Description|
|------------|-----------------|
|**/cdl**|Supprime le contenu du cache de téléchargement.|
|**/f**|Spécifiez cette option avec les options **/i** ou **/il** pour forcer la réinstallation d’un assembly. Si un assembly portant le même nom existe déjà dans le Global Assembly Cache, l'outil le remplace.|
|**/h**[**elp**]|Affiche la syntaxe et les options de commande de l'outil.|
|**/i** *assemblyPath*|Installe un assembly dans le Global Assembly Cache.|
|**/if**  *assemblyPath*|Installe un assembly dans le Global Assembly Cache. Si un assembly portant le même nom existe déjà dans le Global Assembly Cache, l'outil le remplace.<br /><br /> La spécification de cette option revient à spécifier les options **/i** et **/f** ensemble.|
|**/il** *assemblyListFile*|Installe un ou plusieurs assemblys spécifiés dans *assemblyListFile* dans le Global Assembly Cache.|
|**/ir**  *assemblyPath*<br /><br /> *Régime*<br /><br /> *id*<br /><br /> *Description*|Installe un assembly dans le Global Assembly Cache et ajoute une référence pour compter l'assembly. Vous devez spécifier les paramètres *assemblyPath*, *scheme*, *id* et *description* avec cette option. Pour obtenir une description des valeurs valides que vous pouvez spécifier pour ces paramètres, consultez l’option **/r**.<br /><br /> La spécification de cette option revient à spécifier les options **/i** et **/r** ensemble.|
|**/l** [*assemblyName*]|Affiche le contenu du Global Assembly Cache. Si vous spécifiez le paramètre *assemblyName*, l’outil ne répertorie que les assemblys correspondant à ce nom.|
|**/ldl**|Répertorie le contenu du cache de fichiers téléchargés.|
|**/lr** [*assemblyName*]|Répertorie tous les assemblys et leurs décomptes de références correspondants. Si vous spécifiez le paramètre *assemblyName*, l’outil ne répertorie que les assemblys correspondant à ce nom et leurs décomptes de références correspondants.|
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *Régime*<br /><br /> *id*<br /><br /> *Description*|Spécifie une référence avec trace à un assembly ou des assemblys à installer ou à désinstaller. Spécifiez cette option avec les options **/i**, **/il**, **/u** ou **/ul**.<br /><br /> Pour installer un assembly, spécifiez les paramètres *assemblyPath*, *scheme*, *id* et *description* avec cette option. Pour désinstaller un assembly, spécifiez les paramètres *assemblyName*, *scheme*, *id* et *description*.<br /><br /> Pour supprimer une référence à un assembly, vous devez spécifier les mêmes paramètres *scheme*, *id* et *description* que ceux spécifiés avec les options **/i** et **/r** (ou **/ir**) lors de l’installation de l’assembly. Si vous désinstallez un assembly, l'outil supprime également l'assembly du Global Assembly Cache s'il s'agit de la dernière référence à supprimer et si Windows Installer ne possède aucune référence en suspens à l'assembly.<br /><br /> Le paramètre *scheme* spécifie le type de schéma d’installation. Vous pouvez spécifier l'une des valeurs suivantes :<br /><br /> - UNINSTALL_KEY: Spécifiez cette valeur si l’installateur ajoute l’application à Add / Supprimer les programmes dans Microsoft Windows. Les applications s'ajoutent elles-mêmes à Ajout/Suppression de programmes en ajoutant une clé de Registre à HKLM\Software\Microsoft\Windows\CurrentVersion.<br />- FILEPATH: Spécifiez cette valeur si l’installateur n’ajoute pas l’application aux programmes Add/Remove.<br />- OPAQUE : Spécifiez cette valeur si la fourniture d’une clé de registre ou d’un chemin de fichier ne s’applique pas à votre scénario d’installation. Cette valeur vous permet de spécifier des informations personnalisées pour le paramètre *id*.<br /><br /> La valeur à spécifier pour le paramètre *id* dépend de la valeur spécifiée pour le paramètre *scheme* :<br /><br /> - Si vous spécifiez UNINSTALL_KEY pour le paramètre du *système,* spécifiez le nom de l’application définie dans la clé de registre HKLM-Software-Microsoft-Windows-CurrentVersion. Par exemple, si la clé de Registre est HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, spécifiez MyApp pour le paramètre *id*.<br />- Si vous spécifiez FILEPATH pour le paramètre *scheme*, spécifiez le chemin complet du fichier exécutable qui installe l’assembly en tant que paramètre *id*.<br />- Si vous spécifiez OPAQUE pour le paramètre *scheme*, vous pouvez fournir n’importe quelles données en tant que paramètre *id*. Les données que vous spécifiez doivent être mises entre guillemets ("").<br /><br /> Le paramètre *description* vous permet de spécifier un texte descriptif concernant l’application à installer. Ces informations sont affichées lorsque des références sont énumérées.|
|**/silencieux**|Supprime l'affichage de toutes les sorties.|
|**/u**  *assemblyName*|Désinstalle un assembly du Global Assembly Cache.|
|**/uf**  *assemblyName*|Force la désinstallation d'un assembly spécifié en supprimant toutes les références à cet assembly.<br /><br /> La spécification de cette option revient à spécifier les options **/u** et **/f** ensemble. **Remarque :**  Vous ne pouvez pas utiliser cette option pour supprimer un assembly installé à l’aide de Microsoft Windows Installer. Si vous tentez cette opération, l'outil affiche un message d'erreur.|
|**/ul** *assemblyListFile*|Désinstalle un ou plusieurs assemblys spécifiés dans *assemblyListFile* du Global Assembly Cache.|
|**/u**[**ngen**] *assemblyName*|Désinstalle un assembly spécifié du Global Assembly Cache. S'il existe des décomptes de références pour l'assembly spécifié, l'outil les affiche et ne supprime pas l'assembly du Global Assembly Cache. **Remarque :**  Dans le .NET Framework version 2.0, `/ungen` n’est pas pris en charge. Utilisez plutôt la commande `uninstall` de [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md). <br /><br /> Dans le .NET Framework versions 1.0 et 1.1, la spécification de **/ungen** conduit Gacutil.exe à supprimer l’assembly du cache des images natives. Ce cache stocke les images natives pour les assemblys qui ont été créés à l’aide de [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|
|**/ur**  *assemblyName*<br /><br /> *Régime*<br /><br /> *id*<br /><br /> *Description*|Désinstalle une référence à un assembly spécifié du Global Assembly Cache. Pour supprimer une référence à un assemblage, vous devez spécifier le même *schéma,* *id*, et les paramètres *de description* qui ont été spécifiés avec les **options /i** et **/r** (ou **/ir)** lorsque l’assemblage a été installé. Pour obtenir une description des valeurs valides que vous pouvez spécifier pour ces paramètres, consultez l’option **/r**.<br /><br /> La spécification de cette option revient à spécifier les options **/u** et **/r** ensemble.|
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|

## <a name="remarks"></a>Notes 

> [!NOTE]
> Vous devez disposer des droits d'administrateur pour utiliser Gacutil.exe.

Gacutil.exe vous permet plus particulièrement d'installer des assemblys dans le cache, d'en supprimer du cache et de répertorier le contenu du cache.

Gacutil.exe fournit des options qui prennent en charge le décompte de références similaire au modèle de décompte de références pris en charge par Windows Installer. Vous pouvez utiliser Gacutil.exe pour installer deux applications qui installent le même assembly ; l'outil garde la trace du nombre de références à l'assembly. L'assembly reste donc sur l'ordinateur jusqu'à ce que les deux applications soient désinstallées. Si vous utilisez Gacutil.exe pour des installations de produits, utilisez les options qui prennent en charge le décompte de références. Utilisez les options **/i** et **/r** ensemble pour installer un assembly et ajouter une référence pour le décompter. Utilisez les options **/u** et **/r** ensemble pour supprimer un décompte de références pour un assembly. Notez que l’utilisation des options **/i** et **/u** seules ne prend pas en charge le décompte de références. Ces options conviennent à une utilisation pendant le développement d'un produit, mais pas pour des installations de produits.

Utilisez les options **/il** ou **/ul** pour installer ou désinstaller une liste d’assemblys stockés dans un fichier texte ANSI. Le contenu du fichier texte doit être correctement mis en forme. Pour utiliser un fichier texte afin d’installer des assemblys, spécifiez le chemin d’accès de chaque assembly sur une ligne distincte dans le fichier. L'exemple suivant illustre le contenu d'un fichier contenant des assemblys à installer.

```text
myAssembly1.dll
myAssembly2.dll
myAssembly3.dll
```

Pour utiliser un fichier texte afin de désinstaller des assemblys, indiquez le nom qualifié complet de chaque assembly sur une ligne distincte dans le fichier. L'exemple suivant illustre le contenu d'un fichier contenant des assemblys à désinstaller.

```text
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
```

> [!NOTE]
> Si vous tentez d’installer un assembly dont le nom de fichier dépasse les 79-91 caractères (sans compter l’extension du fichier), vous risquez de rencontrer l’erreur suivante :
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> En effet, Gacutil.exe construit en interne un chemin d’accès pouvant atteindre MAX_PATH caractères et composé des éléments suivants :
>
> - GAC Root – 34 caractères (p. ex., `C:\Windows\Microsoft.NET\assembly\`)
> - Architecture – 7 ou 9 caractères (p. ex., `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName – jusqu'à 91 caractères, selon la taille des autres éléments (p. ex., `System.Xml.Linq\`)
> - AssemblyInfo – 31 à 48 caractères ou plus, composés de :
>   - Framework – 5 caractères (p. ex., `v4.0_`)
>   - AssemblyVersion – 8 à 24 caractères (p. ex., `9.0.1000.0_`)
>   - AssemblyLanguage – 1 à 8 caractères (p. ex., `de_`, `sr-Cyrl_`)
>   - PublicKey – 17 caractères (p. ex., `31bf3856ad364e35\`)
> - DllFileName – jusqu'à 91 + 4 caractères (p. ex., `<AssemblyName>.dll`)

## <a name="examples"></a>Exemples

La commande suivante installe l'assembly `mydll.dll` dans le Global Assembly Cache.

```console
gacutil /i mydll.dll
```

La commande suivante supprime l'assembly `hello` du Global Assembly Cache si aucun décompte de références n'existe pour l'assembly.

```console
gacutil /u hello
```

Notez que la commande précédente peut supprimer plusieurs assemblys du cache de l'assembly, car le nom de l'assembly n'est pas complètement spécifié. Par exemple, si les versions 1.0.0.0 et 3.2.2.1 de `hello` sont installées dans le cache, la commande `gacutil /u hello` supprime alors ces deux assemblys.

Suivez l'exemple suivant pour éviter de supprimer plusieurs assemblys. Cette commande supprime uniquement l'assembly `hello` correspondant au numéro de version, à la culture et à la clé publique intégralement spécifiés.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

La commande suivante installe les assemblys spécifiés dans le fichier `assemblyList.txt` du Global Assembly Cache.

```console
gacutil /il assemblyList.txt
```

La commande suivante supprime les assemblys spécifiés dans le fichier `assemblyList.txt` du Global Assembly Cache.

```console
gacutil /ul assemblyList.txt
```

La commande suivante installe `myDll.dll` dans le Global Assembly Cache et ajoute une référence pour le décompter. L'assembly `myDll.dll` est utilisé par l'application `MyApp`. Le paramètre `UNINSTALL_KEY MyApp` spécifie la clé de Registre qui ajoute `MyApp` à Ajout/Suppression de programmes dans Windows. Le paramètre description est spécifié en tant que `My Application Description`.

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

La commande suivante installe `myDll.dll` dans le Global Assembly Cache et ajoute une référence pour le décompter. Le paramètre scheme, `FILEPATH`, et le paramètre id, `c:\applications\myApp\myApp.exe`, spécifient le chemin de l’application qui installe `myDll.dll.`. Le paramètre description est spécifié en tant que `MyApp`.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

La commande suivante installe `myDll.dll` dans le Global Assembly Cache et ajoute une référence pour le décompter. Le paramètre scheme, `OPAQUE`, vous permet de personnaliser les paramètres id et description.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

La commande suivante supprime la référence à `myDll.dll` par l'application `myApp`. S'il s'agit de la dernière référence à l'assembly, elle supprime également l'assembly du Global Assembly Cache.

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

La commande suivante répertorie le contenu du Global Assembly Cache.

```console
gacutil /l
```

## <a name="see-also"></a>Voir aussi

- [Outils](index.md)
- [Cache de l’Assemblée mondiale](../app-domains/gac.md)
- [Regasm.exe (outil d’inscription d’assemblys)](regasm-exe-assembly-registration-tool.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
