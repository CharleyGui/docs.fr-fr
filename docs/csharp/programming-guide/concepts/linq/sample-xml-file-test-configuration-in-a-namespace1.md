---
title: 'Exemple de fichier XML : Configuration de test dans un espace de noms'
description: Ce fichier XML est utilisé dans différents exemples de la documentation de LINQ to XML. Le fichier est un fichier de configuration de test. Le code XML se trouve dans un espace de noms.
ms.date: 07/20/2015
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
ms.openlocfilehash: e08bc476eda39b6e9ff3e2958a49a0d9e5dc303a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302475"
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="c62fc-105">Exemple de fichier XML : Configuration de test dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="c62fc-105">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="c62fc-106">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c62fc-106">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="c62fc-107">Il s'agit d'un fichier de configuration test.</span><span class="sxs-lookup"><span data-stu-id="c62fc-107">This is a test configuration file.</span></span> <span data-ttu-id="c62fc-108">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c62fc-108">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="c62fc-109">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="c62fc-109">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
