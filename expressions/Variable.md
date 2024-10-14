# Varibale Expression

## Abstract

A variable expression is used to specify a varible in place of a operand. It has an ID that is used to identify the variable and on evaluation to substitute a value in place of the variable. Variables are the basic building blocks of a FEF formula.

## Expression Data

The expression parses a single [variable length enum](/binary_types/Variable%20Length%20Enum.md), that indicates the ID of the variable. 

## Expression Result

The result of the expression is of the [`variable`](/datatypes/Variable.md) type with the ID given by the expression data.