--- 

# required metadata 
title: "rxStepPlot function (revoAnalytics) | Microsoft Docs" 
description: " Plot stepwise coefficients for rxLinMod, rxLogit and rxGlm objects. " 
keywords: "(revoAnalytics), rxStepPlot, hplot" 
author: "dphansen"
ms.author: "davidph" 
manager: "cgronlun" 
ms.date: 07/15/2019
ms.topic: "reference" 
ms.prod: "mlserver" 
ms.service: "" 
ms.assetid: "" 

# optional metadata 
ROBOTS: "" 
audience: "" 
ms.devlang: "" 
ms.reviewer: "" 
ms.suite: "" 
ms.tgt_pltfrm: "" 
#ms.technology: "" 
ms.custom: "" 

--- 


 # rxStepPlot: Step Plot 
 ## Description

Plot stepwise coefficients for `rxLinMod`, `rxLogit` and `rxGlm` objects.


 ## Usage

```   
  rxStepPlot(x, plotStepBreaks = TRUE, omitZeroCoefs = TRUE, eps = .Machine$double.eps, 
    main = deparse(substitute(x)), xlab = "Step", ylab = "Stepwise Coefficients", 
    type = "b", pch = "*",
      ...  )

```

 ## Arguments



 ### `x`
  a stepwise regression object of class `rxLinMod`, `rxLogit`, or `rxGlm`with a non-empty `stepCoefs` component, which can be generated by setting the component `keepStepCoefs` of the `variableSelection` argument to `TRUE` when the model is fitted. 



 ### `plotStepBreaks`
  logical value. If `TRUE`, vertical lines are drawn at each step in the stepwise coefficient paths. 



 ### `omitZeroCoefs`
  logical flag. If `TRUE`, coefficients with sum of absolute values less than `eps` will be omitted for plotting. 



 ### `eps`
  the smallest positive floating-point number that is treated as nonzero. 



 ### `main, xlab, ylab, type, pch,  ...`
  additional graphical arguments to be passed directly to the underlying matplot function. 



 ## Value

the nonzero stepwise coefficients are returned invisibly.

 ## Author(s)
 Microsoft Corporation [`Microsoft Technical Support`](https://go.microsoft.com/fwlink/?LinkID=698556&clcid=0x409)


 ## See Also

[rxStepControl](rxStepControl.md),
[rxLinMod](rxLinMod.md),
[rxLogit](rxLogit.md),
[rxGlm](rxGLM.md).

 ## Examples

 ```

  ## setup
  form <- Sepal.Length ~ Sepal.Width + Petal.Length
  scope <- list(
      lower = ~ Sepal.Width,
      upper = ~ Sepal.Width + Petal.Length + Petal.Width * Species)

  ## rxLinMod/variableSelection with keepStepCoefs = TRUE
  varsel <- rxStepControl(method = "stepwise", scope = scope, keepStepCoefs = TRUE)
  rxlm.step <- rxLinMod(form, data = iris, variableSelection = varsel,
      verbose = 1, dropMain = FALSE, coefLabelStyle = "R")
  rxStepPlot(rxlm.step)
```


