---
title: processus d'exécution managée
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
ms.openlocfilehash: bc455817d29d2427f3051e79145b535e3eeaccbb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161099"
---
# <a name="managed-execution-process"></a>processus d'exécution managée
<a name="introduction"></a> Le processus d'exécution managé inclut les étapes suivantes,qui sont décrites en détail plus loin dans cette rubrique :

1. [Choix d'un compilateur](#choosing_a_compiler)

     Pour bénéficier des avantages qu'apporte le Common Language Runtime, vous devez utiliser un ou plusieurs compilateurs de langage ciblant le runtime.

2. [Compilation de votre code en MSIL](#compiling_to_msil)

     La compilation traduit votre code source en langage MSIL (Microsoft Intermediate Language) et génère les métadonnées requises.

3. [Compilation du MSIL en code natif](#compiling_msil_to_native_code)

     Au moment de l'exécution, un compilateur juste-à-temps (JIT) transforme le MSIL en code natif. Au moment de la compilation, le code est soumis à un processus de vérification qui examine le MSIL et les métadonnées afin de déterminer si le code peut être considéré comme étant de type sécurisé.

4. [Exécution de code](#running_code)

     Le Common Language Runtime fournit l'infrastructure qui permet à l'exécution d'avoir lieu et les services pouvant être utilisés pendant l'exécution.

<a name="choosing_a_compiler"></a>
## <a name="choosing-a-compiler"></a>Choix d'un compilateur
 Pour bénéficier des avantages qu'offre le Common Language Runtime (CLR), vous devez utiliser un ou plusieurs compilateurs de langage ciblant le runtime, tels que les compilateurs Visual Basic, C#, Visual C++, F# ou l'un des nombreux compilateurs tiers tels que les compilateurs Eiffel, Perl ou COBOL.

 Dans la mesure où il représente un environnement d'exécution multilangage, le runtime prend en charge une grande variété de types de données et de fonctionnalités de langage. Le compilateur de langage que vous utilisez détermine les fonctionnalités du runtime qui sont disponibles et que vous utilisez pour concevoir votre code. C'est votre compilateur et non le runtime qui établit la syntaxe à laquelle votre code doit se conformer. Si votre composant doit être entièrement utilisable par des composants écrits dans d’autres langages, les types exportés de votre composant doivent exposer uniquement les fonctionnalités de langage qui font partie de la spécification [Language Independence and Language-Independent Components](language-independence-and-language-independent-components.md) . Vous pouvez utiliser l'attribut <xref:System.CLSCompliantAttribute> pour vous assurer que votre code est conforme CLS. Pour plus d'informations, consultez [Language Independence and Language-Independent Components](language-independence-and-language-independent-components.md).

 [Retour au début](#introduction)

<a name="compiling_to_msil"></a>
## <a name="compiling-to-msil"></a>Compilation en MSIL
 Lors d'une compilation destinée à produire du code managé, le compilateur convertit le code source en langage MSIL (Microsoft Intermediate Language), un jeu d'instructions indépendant du processeur qui peut être converti efficacement en code natif. MSIL inclut des instructions pour le chargement, le stockage, l'initialisation et l'appel de méthodes sur des objets, ainsi que des instructions pour la réalisation d'opérations arithmétiques et logiques, le flux de contrôle, l'accès direct à la mémoire, la gestion des exceptions et d'autres opérations. Avant d'exécuter du code, vous devez d'abord convertir le MSIL en code spécifique au processeur, généralement à l'aide d'un [compilateur juste-à-temps (JIT)](#compiling_msil_to_native_code). Dans la mesure où le Common Language Runtime fournit un ou plusieurs compilateurs JIT pour chaque architecture d'ordinateur qu'il prend en charge, le même jeu d'instructions MSIL peut être traité par un compilateur JIT et exécuté sur toute architecture prise en charge.

 Quand un compilateur produit du code MSIL, il génère aussi des métadonnées. Les métadonnées décrivent les types contenus dans votre code, y compris la définition de chaque type, les signatures des membres de chaque type, les membres référencés par votre code, et d'autres données que le runtime utilise au moment de l'exécution. Le MSIL et les métadonnées sont stockés dans un fichier exécutable portable (PE) qui est basé sur le fichier Microsoft PE publié qu'il prolonge et sur le format COFF (Common Object File Format) utilisé traditionnellement pour le contenu exécutable. Ce format de fichier, qui accepte le code MSIL ou le code natif ainsi que les métadonnées, permet au système d'exploitation de reconnaître les images du Common Language Runtime. La présence de métadonnées dans le fichier en même temps que le jeu d'instructions MSIL permet à votre code de se décrire lui-même, ce qui signifie que les bibliothèques de types et IDL (Interface Definition Language) ne sont pas nécessaires. Le runtime recherche les métadonnées dans le fichier et les extrait selon les besoins, au moment de l'exécution.

 [Retour au début](#introduction)

<a name="compiling_msil_to_native_code"></a>
## <a name="compiling-msil-to-native-code"></a>Compilation du MSIL en code natif
 Avant de pouvoir exécuter le langage MSIL (MicroSoft Intermediate Language), vous devez le compiler en code natif avec le Common Language Runtime pour l'architecture de l'ordinateur cible. .NET propose deux méthodes pour effectuer cette conversion :

- Compilateur juste-à-temps (JIT) .NET.

- [Ngen.exe (générateur d’images natives)](../framework/tools/ngen-exe-native-image-generator.md).

### <a name="compilation-by-the-jit-compiler"></a>Compilation par le compilateur JIT
 La compilation JIT convertit à la demande le langage MSIL en code natif au moment de l'exécution de l'application, quand le contenu d'un assembly est chargé et exécuté. Dans la mesure où le Common Language Runtime fournit un compilateur JIT pour chaque architecture de processeur qu'il prend en charge, les développeurs peuvent générer un jeu d'assemblys MSIL pouvant être traité par un compilateur JIT et exécuté sur différents ordinateurs ayant des architectures d'ordinateur différentes. Cependant, si votre code managé appelle des API natives spécifiques à une plateforme ou une bibliothèque de classes spécifique à une plateforme, il s'exécutera sur un système d'exploitation spécifique uniquement.

 La compilation JIT tient compte de la possibilité qu'une partie du code ne soit peut-être jamais appelée au moment de l'exécution. Au lieu de consacrer du temps et des ressources mémoire à la conversion de toutes les instructions MSIL d'un fichier PE en code natif, elle les convertit au fur et à mesure des besoins au moment de l'exécution et stocke le code natif obtenu en mémoire afin qu'il soit accessible pour les appels ultérieurs dans le contexte de ce processus. Le chargeur crée et attache un stub à chaque méthode dans un type quand le type est chargé et initialisé. Quand une méthode est appelée pour la première fois, le stub passe le contrôle au compilateur JIT, qui convertit le MSIL de cette méthode en code natif et modifie le stub afin de pointer directement vers le code natif généré. Par conséquent, les appels suivants à la méthode traitée par le compilateur JIT passent directement au code natif.

### <a name="install-time-code-generation-using-ngenexe"></a>Génération du code d'installation à l'aide de NGen.exe
 Comme le compilateur JIT convertit le MSIL d'un assembly en code natif quand les méthodes individuelles définies dans cet assembly sont appelées, les performances sont nécessairement altérées au moment de l'exécution. Dans la plupart des cas, cette baisse de performances est acceptable. Et surtout, le code généré par le compilateur JIT est lié au processus qui a déclenché la compilation. Il ne peut pas être partagé entre plusieurs processus. Pour que le code généré puisse être partagé entre plusieurs appels d'une application ou entre plusieurs processus partageant un jeu d'assemblys, le Common Language Runtime prend en charge un mode de compilation à l'avance. Ce mode de compilation à l’avance utilise [Ngen.exe (générateur d’images natives)](../framework/tools/ngen-exe-native-image-generator.md) pour convertir les assemblys MSIL en code natif de façon similaire au compilateur JIT. Toutefois, le fonctionnement de Ngen.exe diffère de celui du compilateur JIT sur trois points :

- Il exécute la conversion de MSIL en code natif avant d'exécuter l'application et non pendant l'exécution de celle-ci.

- Il compile un assembly entier à la fois, au lieu d'une méthode à la fois.

- Il conserve le code généré dans le cache des images natives comme un fichier sur le disque.

### <a name="code-verification"></a>Vérification du code
 Dans le cadre de sa compilation en code natif, le code MSIL est soumis à un processus de vérification, sauf si un administrateur a établi une stratégie de sécurité qui autorise le code à ignorer ce processus. La vérification examine le MSIL et les métadonnées afin de déterminer si le code est de type sécurisé, ce qui signifie qu'il ne doit accéder qu'aux emplacements de mémoire autorisés. La sécurité de type permet d'isoler les objets les uns des autres et de les protéger de toute altération accidentelle ou malveillante. Elle garantit également que les restrictions liées à la sécurité peuvent être appliquées au code de manière fiable.

 Le runtime s'appuie sur le fait que les instructions suivantes sont vraies pour le code de type sécurisé vérifié :

- une référence à un type qui est strictement compatible avec le type référencé ;

- seules les opérations définies de façon appropriée sont appelées pour un objet ;

- les identités sont conformes à ce qu'elles prétendent être.

 Pendant le processus de vérification, le code MSIL est examiné en vue d'essayer de confirmer qu'il peut accéder aux emplacements de mémoire et appeler des méthodes uniquement par le biais de types correctement définis. Par exemple, le code n'autorise pas l'accès aux champs d'un objet d'une manière qui accepte le débordement de capacité des emplacements de mémoire. Par ailleurs, le processus de vérification inspecte le code MSIL afin de déterminer s'il a été généré correctement, car un code MSIL incorrect peut donner lieu à une violation des règles de sécurité des types. Le processus de vérification passe un jeu de code de type sécurisé et correctement défini, et ne passe que du code de ce type. Cependant, une partie du code de type sécurisé peut ne pas passer le test de vérification avec succès en raison de certaines limitations du processus de vérification, et certains langages, de par leur design, ne produisent pas un code de type sécurisé vérifié. Si le code de type sécurisé est requis par la stratégie de sécurité, mais qu'il ne passe pas le test de vérification avec succès, une exception est levée quand le code est exécuté.

 [Retour au début](#introduction)

<a name="running_code"></a>
## <a name="running-code"></a>Exécution de code
 Le Common Language Runtime fournit l'infrastructure qui permet à l'exécution managée d'avoir lieu et les services pouvant être utilisés pendant l'exécution. Pour qu'une méthode puisse être exécutée, elle doit d'abord être compilée en un code spécifique au processeur. Chaque méthode pour laquelle le MSIL a été généré est compilée juste-à-temps quand elle est appelée pour la première fois, puis s'exécute. Quand la méthode est exécutée la fois suivante, le code natif existant traité par le compilateur JIT est exécuté. Le processus de compilation JIT puis d'exécution du code est répété jusqu'à ce que l'exécution soit complètement terminée.

 Pendant l'exécution, le code managé bénéficie de services tels que le garbage collection, la sécurité, l'interopérabilité avec le code non managé, la prise en charge du débogage interlangage ainsi que la prise en charge améliorée du déploiement et du versioning.

 Dans Microsoft Windows Vista, le chargeur du système d’exploitation recherche des modules managés en examinant un bit dans l’en-tête COFF. Le bit défini indique un module managé. Si le chargeur détecte des modules managés, il charge mscoree.dll. `_CorValidateImage` et `_CorImageUnloading` informent le chargeur quand les images de modules managés sont chargées et déchargées. `_CorValidateImage` effectue les actions suivantes :

1. garantit que le code est du code managé valide ;

2. change le point d'entrée dans l'image en point d'entrée dans le runtime.

 Sous Windows 64 bits, `_CorValidateImage` modifie l'image en mémoire en la transformant du format PE32 au format PE32+.

 [Retour au début](#introduction)

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble](../framework/get-started/overview.md)
- [Indépendance du langage et composants indépendants du langage](language-independence-and-language-independent-components.md)
- [Métadonnées et composants de Self-Describing](metadata-and-self-describing-components.md)
- [Ilasm.exe (assembleur IL)](../framework/tools/ilasm-exe-il-assembler.md)
- [Sécurité](security/index.md)
- [Interopération avec du code non managé](../framework/interop/index.md)
- [Déploiement](../framework/deployment/net-framework-applications.md)
- [Assemblys dans .NET](assembly/index.md)
- [Domaines d'application](../framework/app-domains/application-domains.md)
