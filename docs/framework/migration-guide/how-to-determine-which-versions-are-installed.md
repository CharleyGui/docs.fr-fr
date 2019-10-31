---
title: Guide pratique pour déterminer les versions du .NET Framework installées
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: e339767b981cea80b1b804db7360961dc42f2102
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126323"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Guide pratique pour déterminer les versions du .NET Framework installées

Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions du .NET Framework sur leurs ordinateurs. Quand vous développez ou déployez votre application, vous pouvez avoir besoin de savoir quelles versions de .NET Framework sont installées sur l'ordinateur de l'utilisateur.

Le .NET Framework comporte deux principaux composants, dont les versions sont définies séparément :

- Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications. .NET Framework et les assemblys partagent le même numéro de version.

- Le Common Language Runtime (CLR), qui gère et exécute le code de votre application. Le CLR est identifié par son propre numéro de version (consultez [versions et dépendances](versions-and-dependencies.md)).

> [!NOTE]
> Chaque nouvelle version du .NET Framework conserve les fonctionnalités des versions antérieures et en ajoute de nouvelles. Vous pouvez charger plusieurs versions du .NET Framework sur un seul ordinateur en même temps, ce qui signifie que vous pouvez installer le .NET Framework sans avoir à désinstaller les versions antérieures. En règle générale, il est préférable de ne pas désinstaller les versions antérieures du .NET Framework, car une application que vous utilisez peut dépendre d’une version spécifique et risquer de dysfonctionner si cette version est supprimée.
>
> Il existe une différence entre la version du .NET Framework et la version du CLR :
>
> - La version du .NET Framework dépend du jeu d’assemblys qui constituent la bibliothèque de classes du .NET Framework. Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.
> - La version du CLR dépend du runtime sur lequel les applications .NET Framework s’exécutent. En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework. Par exemple, le CLR version 4.0.30319.*xxxxx* prend en charge les versions 4 à 4.5.2 du .NET Framework, où *xxxxx* est inférieur à 42000, tandis que le CLR version 4.0.30319.42000 prend en charge toutes les versions du .NET Framework à partir de .NET Framework 4.6.
>
> Pour plus d’informations sur les versions, consultez [Versions et dépendances du .NET Framework](versions-and-dependencies.md).

Pour obtenir la liste des versions du .NET Framework installées sur un ordinateur, accédez au Registre. Vous pouvez utiliser l’Éditeur du Registre pour voir le Registre ou utiliser du code pour l’interroger :

- Identifiez les versions les plus récentes du .NET Framework (4.5 et versions ultérieures) :
  - [Utiliser l’Éditeur du Registre pour déterminer les versions du .NET Framework](#net_b)
  - [Utiliser du code pour interroger le Registre sur les versions du .NET Framework](#net_d)
  - [Utiliser PowerShell pour interroger le Registre sur les versions du .NET Framework](#ps_a)
- Identifiez des versions antérieures du .NET Framework (1&#8211;4) :
  - [Utiliser l’Éditeur du Registre pour déterminer les versions du .NET Framework](#net_a)
  - [Utiliser du code pour interroger le Registre sur les versions du .NET Framework](#net_c)

Pour obtenir la liste des versions du CLR installées sur un ordinateur, utilisez un outil ou du code :

- [Utiliser l’outil Clrver](#clr_a)
- [Utiliser du code pour interroger la classe Environment](#clr_b)

Pour plus d’informations sur la détection des mises à jour installées pour chaque version du .NET Framework, consultez [procédure : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Identifier les versions les plus récentes du .NET Framework (4.5 et versions ultérieures)

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Identifier les versions 4.5 et ultérieures de .NET Framework dans le Registre

1. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

     Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.

2. Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. Si la sous-clé **Full** est absente, alors .NET Framework 4.5 n’est pas installé ni une version ultérieure.

    > [!NOTE]
    > Le dossier **NET Framework Setup** du Registre ne commence *pas* par un point.

3. Recherchez une entrée DWORD nommée **Release**. Si elle existe, alors .NET Framework 4.5 ou des versions ultérieures sont installés. Sa valeur est une clé de version correspondant à une version particulière du .NET Framework. Dans l’illustration suivante, par exemple, la valeur de l’entrée **Release** est *378389*, à savoir la clé de version de .NET Framework 4.5.

     ![Entrée de Registre pour le .NET Framework 4,5](./media/clr-installdir.png "Entrée de Registre pour le .NET Framework 4,5")

Le tableau suivant présente la valeur DWORD **Version** sur les différents systèmes d’exploitation pour .NET Framework 4.5 et les versions ultérieures.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Version du .NET Framework|Valeur du paramètre DWORD Release|
|--------------------------------|-------------|
|.NET Framework 4.5|Tous les systèmes d’exploitation Windows : 378389|
|.NET Framework 4.5.1|Sur Windows 8.1 et Windows Server 2012 R2:378675<br />Sur tous les autres systèmes d’exploitation Windows : 378758|
|.NET Framework 4.5.2|Tous les systèmes d’exploitation Windows : 379893|
|.NET Framework 4.6|Sur Windows 10:393295<br />Sur tous les autres systèmes d’exploitation Windows : 393297|
|.NET Framework 4.6.1|Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254<br />Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10) : 394271|
|.NET Framework 4.6.2|Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806|
|.NET Framework 4.7|Sur Windows 10 Creators Update : 460798<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805|
|.NET Framework 4.7.1|Sur Windows 10 automne Creators Update et Windows Server, version 1709:461308<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310|
|.NET Framework 4.7.2|Sur Windows 10 avril 2018 mise à jour et Windows Server, version 1803:461808<br/>Sur tous les systèmes d’exploitation Windows autres que Windows 10 avril 2018 Update et Windows Server, version 1803:461814|
|.NET Framework 4.8|Sur Windows 10 mai 2019 mise à jour et Windows 10 novembre 2019 mise à jour : 528040<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049|

Vous pouvez utiliser ces valeurs de différentes manières :

- Pour déterminer si une certaine version de .NET Framework est installée sur une certaine version du système d’exploitation Windows, regardez si la valeur DWORD **Version** est *égale à* la valeur indiquée dans le tableau. Par exemple, pour déterminer si .NET Framework 4.6 est présent sur un système Windows 10, regardez si la valeur **Version** est *égale à* 393295.

- Pour déterminer s’il existe une version minimale de .NET Framework, utilisez la plus petite valeur DWORD **Version** de cette version. Par exemple, si votre application s’exécute sur .NET Framework 4.6 ou une version ultérieure, recherchez une valeur DWORD **Version** *supérieure ou égale à* 393295. Vous trouverez un tableau qui présente uniquement la valeur DWORD **Version** minimale pour chaque version de .NET Framework dans [Valeurs DWORD Version minimales pour .NET Framework 4.5 et les versions ultérieures](minimum-release-dword.md).

- Pour tester plusieurs versions, commencez par rechercher une valeur *supérieure ou égale à* la plus petite valeur DWORD de la dernière version de .NET Framework, puis comparez-la avec la plus petite valeur DWORD de chacune des versions antérieures, en allant de la plus récente à la plus ancienne. Par exemple, si votre application exige .NET Framework 4.7 ou une version ultérieure et que vous souhaitez identifier la version installée de .NET Framework, commencez par rechercher une valeur DWORD **Version** *supérieure ou égale à* 461808 (la plus petite valeur DWORD pour .NET Framework 4.7.2). Ensuite, comparez la valeur DWORD **Version** avec la plus petite valeur de chaque version ultérieure de .NET Framework. Vous trouverez un tableau qui présente uniquement la valeur DWORD **Version** minimale pour chaque version de .NET Framework dans [Valeurs DWORD Version minimales pour .NET Framework 4.5 et les versions ultérieures](minimum-release-dword.md).

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a>Identifier les versions 4.5 et ultérieures de .NET Framework avec du code

1. Utilisez les méthodes <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> et <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> pour accéder à la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** dans le Registre Windows.

    L’existence de l’entrée DWORD **Release** dans la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** indique que .NET Framework 4.5 ou une version ultérieure sont installés sur un ordinateur.

2. Vérifiez la valeur de l’entrée **Release** pour déterminer la version installée. Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).

L’exemple suivant vérifie la valeur de l’entrée **Release** dans le Registre pour identifier les versions 4.5 et ultérieures du .NET Framework installées :

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Cet exemple suit la pratique recommandée concernant la vérification de version :

- Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.

- Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Rechercher une version minimale exigée du .NET Framework (4.5 ou ultérieure) avec PowerShell

- Utilisez des commandes PowerShell pour vérifier la valeur de l’entrée **Release** de la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.

Les exemples suivants vérifient la valeur de l’entrée **Release** pour déterminer si .NET Framework 4.6.2 ou une version ultérieure sont installés. Ce code retourne `True` s’il est installé et `False` dans le cas contraire.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Pour rechercher une autre version minimale exigée du .NET Framework, remplacez *394802* dans ces exemples par une valeur **Release** indiquée dans le [tableau des versions du .NET Framework](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Identifier des versions antérieures du .NET Framework (1&#8211;4)

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a>Identifier les versions 1&#8211;4 du .NET Framework dans le Registre

1. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

    Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.

2. Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:

    - Pour les versions 1.1 à 3.5 du .NET Framework, chaque version installée est listée en tant que sous-clé sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**. Par exemple, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. Le numéro de version est stocké sous forme de valeur dans l’entrée **Version** de la sous-clé de version.

    - Pour .NET Framework 4, l’entrée **Version** se trouve sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** ou sous les deux sous-clés.

    > [!NOTE]
    > Le dossier d’installation **NET Framework Setup** dans le Registre ne commence pas par un point.

    La figure suivante illustre la sous-clé et son entrée **Version** pour .NET Framework 3.5.

    ![Entrée de Registre pour le .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 et versions antérieures")

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a>Identifier les versions 1&#8211;4 du .NET Framework avec du code

- Utilisez la classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pour accéder à la sous-clé **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** dans le Registre Windows.

L’exemple suivant identifie les versions .NET Framework 1&#8211;4 installées :

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Identifier les versions du CLR

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a>Identifier la version actuelle du CLR avec Clrver.exe

Utilisez l’[outil de version CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur :

- À partir d’une [invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md), entrez `clrver`.

    Résultat de l'exemple :

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a>Identifier la version actuelle du CLR avec la classe Environment

> [!IMPORTANT]
> Pour .NET Framework 4.5 et ultérieur, n’utilisez pas la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour détecter la version du CLR. Interrogez plutôt le Registre comme décrit dans [Identifier les versions 4.5 et ultérieures du .NET Framework avec du code](#net_d).

1. Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.

    L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code. Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.

    Pour les versions 4, 4.5, 4.5.1 et 4.5.2 du .NET Framework, la représentation sous forme de chaîne de l’objet <xref:System.Version> retourné a la forme 4.0.30319.*xxxxx*, où *xxxxx* est inférieur à 42000. Pour les versions 4.6 et ultérieures du .NET Framework, la forme est 4.0.30319.42000.

2. Une fois que vous avez l’objet `Version`, interrogez-le comme suit :

   - Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.

   - Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

   - Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code. Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.

L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Voir aussi

- [Comment : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md)
- [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md)
- [Versions et dépendances du .NET Framework](versions-and-dependencies.md)
