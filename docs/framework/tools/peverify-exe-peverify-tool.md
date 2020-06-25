---
title: Peverify.exe (outil PEVerify)
description: Utilisez Peverify.exe (contrôle exécutable portable) pour déterminer si le code MSIL (Microsoft Intermediate Language) & les métadonnées répondent aux normes de sécurité de type dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: 478c04a45c7f9d3ad568a6bc4a12a89fe786583a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325627"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (outil PEVerify)

L’outil PEVerify Tool permet aux développeurs qui génèrent du langage MSIL (Microsoft Intermediate Language) (tels que les writers de compilateur et les développeurs de moteur de script) de déterminer si leur code MSIL et les métadonnées associées répondent aux exigences de sécurité de type. Certains compilateurs génèrent du code de type sécurisé vérifié uniquement si vous évitez d'utiliser certaines constructions de langage. Si vous utilisez un tel compilateur, vous souhaiterez peut-être vérifier que vous n’avez pas compromis la sécurité de type de votre code. Vous pouvez exécuter l’outil PEVerify sur vos fichiers pour vérifier le langage MSIL et les métadonnées.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).
  
## <a name="syntax"></a>Syntaxe  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Argument|Description|  
|--------------|-----------------|  
|*extension*|Fichier exécutable portable dont le langage MSIL et les métadonnées sont à vérifier.|  
  
|Option|Description|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|Abandonne la vérification si le nombre d’erreurs atteint *maxErrorCount* erreurs.<br /><br /> Ce paramètre n'est pas pris en charge dans les versions 2.0 et ultérieures du .NET Framework.|  
|**/clock**|Calcule et indique la durée des vérifications suivantes, en millisecondes :<br /><br /> **MD Val. cycle**<br /> Cycle de validation des métadonnées<br /><br /> **MD Val. pure**<br /> Validation simple des métadonnées<br /><br /> **IL Ver. cycle**<br /> Cycle de vérification MSIL<br /><br /> **IL Ver pure**<br /> Vérification MSIL simple<br /><br /> Les temps **MD Val. cycle** et **IL Ver. cycle** incluent le temps qu’il faut pour effectuer les procédures de démarrage et d’arrêt nécessaires. Les temps **MD Val. pure** et **IL Ver pure** reflètent le temps qu’il faut pour effectuer la validation ou la vérification uniquement.|  
|**/Help**|Affiche la syntaxe et les options de commande de l'outil.|  
|**/hresult**|Affiche les codes d'erreur au format hexadécimal.|  
|**/ignore=** *hex.code* [, *hex.code*]|Ignore les codes d'erreur spécifiés.|  
|**/ignore=@** *responseFile*|Ignore les codes d'erreur répertoriés dans le fichier réponse spécifié.|  
|**/Il**|Procède aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l’assembly spécifié par *filename*. L’outil retourne les descriptions détaillées de chaque problème rencontré, sauf si vous spécifiez l’option **/quiet**.|  
|**/MD**|Procède aux contrôles de validation des métadonnées sur l’assembly spécifié par *filename*. Cette option parcourt la structure de métadonnées complète dans le fichier et signale tous les problèmes de validation rencontrés.|  
|**/nologo**|Supprime l'affichage de version de produit et d'informations de copyright.|  
|**/nosymbols**|Dans le .NET Framework version 2.0, il supprime les numéros de ligne pour la compatibilité descendante.|  
|**/quiet**|Spécifie le mode silencieux ; supprime la sortie des états sur les problèmes de vérification. Peverify.exe continue à indiquer si le fichier est de type sécurisé, mais ne fait pas état d'informations sur les problèmes empêchant la vérification de la sécurité de type.|  
|`/transparent`|Vérifiez uniquement les méthodes transparentes.|  
|**/unique**|Ignore les codes d'erreur récurrents.|  
|**/verbose**|Dans le .NET Framework version 2.0, il affiche des informations supplémentaires dans les messages de vérification MSIL.|  
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## <a name="remarks"></a>Remarques  
 Le Common Language Runtime repose sur l'exécution de type sécurisé du code de l'application pour permettre de mettre en œuvre des mécanismes de sécurité et d'isolation. Le code qui n’est pas de [type sécurisé vérifié](../../standard/security/key-security-concepts.md#type-safety-and-security) ne peut normalement pas être exécuté, même si vous pouvez définir une stratégie de sécurité permettant l’exécution d’un code de confiance, mais non vérifiable.  
  
 Si ni l’option **/md** ni l’option **/il** ne sont spécifiées, Peverify.exe effectue ces deux types de contrôles. Peverify.exe procède en premier lieu aux contrôles **/md**. En l’absence d’erreurs, il effectue ensuite les contrôles **/il**. Si vous spécifiez à la fois les contrôles **/md** et **/il**, les contrôles **/il** sont effectués, y compris en cas d’erreurs dans les métadonnées. En l’absence d’erreurs dans les métadonnées, **peverify** *filename* équivaut alors à **peverify** *filename* **/md** **/il**.  
  
 Peverify.exe effectue des contrôles de vérification MSIL complets en fonction de l'analyse des flux de données et d'une liste de plusieurs centaines de règles sur la validité des métadonnées. Pour plus d’informations sur les contrôles effectués par Peverify.exe, consultez « Metadata Validation Specification » et « MSIL Instruction Set Specification » dans le dossier « Tool Developer’s Guide » du SDK Windows.  
  
.NET Framework version 2,0 ou ultérieure prend en charge `byref` les retours vérifiables spécifiés à l’aide des instructions MSIL suivantes : `dup` ,,,, `ldsflda` `ldflda` `ldelema` `call` et `unbox` .  
  
## <a name="examples"></a>Exemples  
 La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`.  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Une fois les contrôles ci‑dessus terminés, Peverify.exe affiche le message suivant.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`. L'outil affiche le temps requis pour effectuer ces vérifications.  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 Une fois les contrôles ci‑dessus terminés, Peverify.exe affiche le message suivant.  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`. Toutefois, Peverify.exe s'arrête lorsqu'il atteint le nombre d'erreurs maximal de 100. L'outil ignore également les codes d'erreur spécifiés.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 La commande suivante aboutit au même résultat que dans l'exemple précédent, mais elle spécifie les codes d'erreur à ignorer dans le fichier réponse `ignoreErrors.rsp`.  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Le fichier réponse peut comporter une liste de codes d'erreur avec la virgule comme séparateur.  
  
```text
0x12345678, 0xABCD1234  
```  
  
 Le fichier réponse peut également être mis en forme avec un code d'erreur par ligne.  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Écriture de code de type sécurisé vérifié](../misc/code-access-security-basics.md#typesafe_code)
- [Cohérence des types et sécurité](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Invites de commandes](developer-command-prompt-for-vs.md)
