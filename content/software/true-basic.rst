True BASIC
##########
:date: 2015-04-26 17:31
:author: jmercouris
:category: Software
:slug: true-basic
:status: published

True BASIC was one of the first languages that I learned in school. True
BASIC, isn't an extremely powerful language or with many applications,
but it is a language that is effective in teaching some of the basics of
programming to new students. Eventually students will move onto
different languages. I've decided to open source all of my programs to
reflect on some of the good and bad things about the source code I've
written, and how I've changed as a developer since then.

 

Let's go through an example of a program I wrote then and check out what
things I did well, and things that I would change now as a developer.

 

::

    !__________________________________________________________
    !
    ! Program Written by John Mercouris
    !__________________________________________________________
    !
    ! This program organizes a garage sale and keeps track
    ! of what items have been sold and which items are still
    ! for sale.
    !__________________________________________________________
    !
    ! Variables Used:
    !
    ! StockNumber(): Stock Number of a product.
    ! Itemname$ (): Name of item
    ! Price (): Price of object
    ! Ifsold() (): Array denoting if an item has been sold
    !__________________________________________________________ 
    !
    ! Sub Programs
    !
    ! SellstockNumber: Sell an item by stock number by calling sub
    ! SellName : Sell an item by name by callin sub
    ! SearchByName : Search for an item by name with this sub
    ! ItemsSold : A printout of all items sold and revenue generated
    ! ItemsNotSold : All items not sold , but values of items printed
    !__________________________________________________________

To begin with, the header is extremely informative, but perhaps too much
so. Many IDEs and #def blocks automatically create a listing of methods
available in a file (think Eclipse outline view). In a lower level
language or with an unsophisticated IDE/text editor, this is crucial to
browsing files.

Also very important is the Variables Used section. While it shouldn't be
called variables used, your declaration of your class level variables
should almost always occur at the top of the file. When confusing or
non-obvious variables should be commented or renamed.

::

    CLEAR
    DIM StockNumber(10000), ItemName$(10000), Price(10000), IfSold(100000)

    DO While More Data
     LET X = X + 1
     READ ItemName$(x), StockNumber(x), Price(x), IfSold(x)
    LOOP

    CALL ShellSort (ItemName$(), StockNumber(), Price(),x, IfSold())

When writing a program with assumptions, those assumptions should be
clarified in comments. For example, in this case, why is there a shell
sort being called on the stock items? Does the program rely on the items
being sorted? Is this useful for the user or the managing data
structure?

::

    DO while choice <> 6

     CALL Menu
     PRINT
     INPUT Prompt "Enter a choice from the menu above using it's number denotation.":Choice

     SELECT CASE Choice

     CASE is = 1
     CALL SellStockNumber (ItemName$(), StockNumber(), Price(),x, IfSold())
     CASE is = 2
     CALL SellName (ItemName$(), StockNumber(), Price(),x, IfSold())
     CASE is = 3
     CALL SearchByName (ItemName$(), StockNumber(), Price(),x, IfSold())
     CASE is = 4
     CALL ITEMSSOLD (ItemName$(), StockNumber(), Price(),x, IfSold())
     CASE is = 5
     CALL ItemsNotSold (ItemName$(), StockNumber(), Price(),x, IfSold())
     CASE is = 6

     CASE else
     END SELECT

    LOOP

The above is a good usage of a main loop within a program. All of the
menu subroutines are broken up into separate callbacks. This makes the
code easily editable and extensible.

::

    !__________________________________________________________
    ! Stock Numbers
    !_________________
    !
    ! John - 1000
    ! Andrew - 2000
    ! Theodosia - 3000
    ! Takis - 4000
    !__________________________________________________________
    ! Item Name Stock Number Price IfSold
    !__________________________________________________________

    DATA Go Cart, 1001, 800, 0
    DATA R/C Airplane, 1002, 200, 0
    DATA Dell 273 A, 1003, 600, 0
    DATA Projector, 1004, 400, 0
    DATA Motherboard, 1006, 25, 0
    DATA PS2, 1005, 80, 0
    DATA Paintball Gun, 2001, 300, 0
    DATA Dino GT Trick Bike, 2002, 100, 0
    DATA Coffee Pot, 3001, 20, 0
    DATA Necklace, 3002, 80, 0
    DATA Gateway 2000, 3003, 5, 0
    DATA LG Computer, 3004, 300, 0
    DATA Micron Computer, 4001, 10, 0
    DATA Bicycle, 4002, 40, 0
    DATA CRT Tv, 4003, 300, 0

    END

The above is an example of bad programming. Naming things with constants
as data tags embedded in the program is not a good idea. While it is
more complex to load your data from a database or a text file it is much
more safe. A careless edit from a developer can result in data being
lost. In addition it doesn't afford flexibility when changing back and
forth from different change sets. It may be that you have to roll back
your software but in doing so you lose all of your "data" that you
embedded into your program. Unfortunately the above example cannot be
easily remedied due to the constraints of programming in True BASIC

::

    !______________________________________________________________________________
    !
    ! Shell Sort
    !______________________________________________________________________________

    SUB ShellSort (ItemName$(), StockNumber(), Price(),x, IfSold())

     LET Gap = INT(X / 2)
     DO While Gap <> 0
     LET Flag = 1

     FOR Count = 1 to (X - Gap)

     IF ItemName$(Count) > ItemName$(Count + Gap) THEN

     LET Temp$ = ItemName$(Count)
     LET ItemName$(count) = ItemName$(count + gap)
     LET ItemName$(count + gap) = Temp$

     LET Temp = StockNumber(Count)
     LET StockNumber(count) = StockNumber(count + gap)
     LET StockNumber(count + gap) = Temp

     LET Temp = Price(Count)
     LET Price(count) = Price(count + gap)
     LET Price(count + gap) = Temp

     LET Temp = IfSold(Count)
     LET IfSold(count) = IfSold(count + gap)
     LET IfSold(count + gap) = Temp

     LET Flag = 0
     END IF

     NEXT Count
     IF Flag = 1 Then
     LET Gap = INT(Gap / 2)
     END IF
     LOOP


    END SUB

When possible, always group together functionally related sections of
your program. In this case, shell sort is not strongly tied to my garage
sale program. Sorting is a abstract/general function that I need my
program to be able to do. It would be ideal to break this apart into
another file and use it as part of a library.

::

    !______________________________________________________________________________
    !
    ! Menu
    !______________________________________________________________________________


    SUB Menu

     CLEAR
     PRINT "__________________________________________"
     PRINT "| Garage Sale Menu |"
     PRINT "|________________________________________|"
     PRINT "| 1. Sell an item with stocknumber. |"
     PRINT "| 2. Sell an item by name. |"
     PRINT "| 3. Search for an item. |"
     PRINT "| 4. Items sold and profit made. |"
     PRINT "| 5. Items not sold. |"
     PRINT "| 6. Quit |"
     PRINT "|________________________________________|"

    END SUB

    !______________________________________________________________________________
    !
    ! Sell by stock number
    !______________________________________________________________________________


    SUB SellStockNumber (ItemName$(), StockNumber(), Price(),x, IfSold())
     CLEAR
     PRINT "___________________________________________________________"
     PRINT "|Items left to sell |"
     PRINT "|_________________________________________________________|"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"
     FOR Z = 1 to X
     IF IfSold(Z) = 0 Then
     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Z), StockNumber(Z), Price(Z)
     PRINT "|_________________________________________________________|"
     END IF
     NEXT Z
     PRINT "|_________________________________________________________|"
     PRINT
     INPUT Prompt "Enter the Stock Number of the item you wish to sell, or type N to cancel.":Search


     LET Low = 1
     LET Middle = 1
     LET High = x
     DO while Search <> StockNumber(Middle) and Low <= High
     LET Middle = Int((Low + High)/2)
     IF Search < StockNumber(Middle) THEN
     LET High = Middle - 1
     END IF

     IF Search > StockNumber(Middle) THEN

     LET Low = MIddle + 1
     END IF
     LOOP
     IF Search = StockNumber(Middle) THEN
     CLEAR
     PRINT "___________________________________________________________"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"

     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Middle), StockNumber(Middle), Price(Middle)

     PRINT "|_________________________________________________________|"
     LET IfSold(Middle) = 1
     PRINT "Press any key to Continue."

The functionality of printing should be broken up into its own
subroutine. In this case, printing is a non trivial task requiring
several formatting operations to be done. It is coupled into a
subroutine with unrelated logic. This makes the program bloated and
difficult to edit. It would be ideal to break apart the printing into
almost a separate file. The separate file would have an abstract
printing operating where you could print a "window" with some sort of
title. Then, the variables and their labels that you would like to
print. In an abstract way you could reconstruct every window in this
program.

::

     ELSE
     CLEAR
     PRINT "No results were found for your query."
     PRINT "Press any key to continue."

     END IF

     GET KEY Pse
    END SUB

    !__________________________________________________________
    !
    ! Sell by name
    !__________________________________________________________

    SUB SellName (ItemName$(), StockNumber(), Price(),x, IfSold())

     CLEAR
     PRINT "___________________________________________________________"
     PRINT "|Items left to sell |"
     PRINT "|_________________________________________________________|"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"
     FOR Z = 1 to X
     IF IfSold(Z) = 0 Then
     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Z), StockNumber(Z), Price(Z)
     PRINT "|_________________________________________________________|"
     END IF
     NEXT Z
     PRINT "|_________________________________________________________|"
     PRINT
     INPUT Prompt "Type the name exactly as it appears using appropriate capitals, spaces etc.":Search$


     LET Low = 1
     LET Middle = 1
     LET High = x
     DO while Search$ <> ItemName$(Middle) and Low <= High
     LET Middle = Int((Low + High)/2)
     IF Search$ < ItemName$(Middle) THEN
     LET High = Middle - 1
     END IF

     IF Search$ > ItemName$(Middle) THEN

     LET Low = Middle + 1
     END IF
     LOOP
     IF Search$ = ItemName$(Middle) THEN
     CLEAR
     PRINT "___________________________________________________________"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"

     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Middle), StockNumber(Middle), Price(Middle)

     PRINT "|_________________________________________________________|"
     LET IfSold(Middle) = 1
     PRINT "Press any key to Continue."

     ELSE
     CLEAR
     PRINT "No results were found for your query."
     PRINT "Press any key to continue."

     END IF

     GET KEY Pse


    END SUB

This example is of a subroutine that is far too long. Unfortunately one
of the curses of BASIC is the limit of how it can combine subroutines
and files.

::

    !______________________________________________________________________________
    !
    ! Search By Name
    !______________________________________________________________________________

    SUB SearchByName (ItemName$(), StockNumber(), Price(),x, IfSold())


     CLEAR
     PRINT "___________________________________________________________"
     PRINT "|Items left to sell |"
     PRINT "|_________________________________________________________|"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"
     FOR Z = 1 to X
     IF IfSold(Z) = 0 Then
     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Z), StockNumber(Z), Price(Z)
     PRINT "|_________________________________________________________|"
     END IF
     NEXT Z
     PRINT "|_________________________________________________________|"


     INPUT Prompt "Type the name exactly, spacing every word and capitalize the first letter of every word as well: ":Search$


     LET Low = 1
     LET Middle = 1
     LET High = x
     DO while Search$ <> ItemName$(Middle) and Low <= High
     LET Middle = Int((Low + High)/2)
     IF Search$ < ItemName$(Middle) THEN
     LET High = Middle - 1
     END IF

     IF Search$ > ItemName$(Middle) THEN

     LET Low = Middle + 1
     END IF
     LOOP
     IF Search$ = ItemName$(Middle) THEN
     CLEAR
     PRINT "___________________________________________________________"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"

     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Middle), StockNumber(Middle), Price(Middle)

     PRINT "|_________________________________________________________|"
     LET IfSold(Middle) = 1


     ELSE
     CLEAR
     PRINT "No results were found for your query."
     END IF
     PRINT "Press any Key to Continue"
     GET KEY pse
    END SUB

    !__________________________________________________________
    !
    ! Items Sold
    !__________________________________________________________

    SUB ItemsSold (ItemName$(), StockNumber(), Price(),x, IfSold())

     CLEAR
     PRINT "___________________________________________________________"
     PRINT "|Items Sold |"
     PRINT "|_________________________________________________________|"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"
     FOR Z = 1 to X
     IF IfSold(Z) = 1 Then
     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Z), StockNumber(Z), Price(Z)
     LET TotalProfit = TotalProfit + Price(Z)
     PRINT "|_________________________________________________________|"
     END IF
     NEXT Z
     PRINT "|_________________________________________________________|"
     PRINT USING "Total Profit Earned was ###,###,###.##":TotalProfit
     PRINT
     PRINT "Press any key to continue"
     GET KEY pse
    END SUB

    !______________________________________________________________________________
    !
    ! Items not sold
    !______________________________________________________________________________

    SUB ItemsNotSold (ItemName$(), StockNumber(), Price(),x, IfSold())



     CLEAR
     PRINT "___________________________________________________________"
     PRINT "|Items left to sell |"
     PRINT "|_________________________________________________________|"
     PRINT "| Name of Item Stock Number Price |"
     PRINT "|_________________________________________________________|"
     FOR Z = 1 to X
     IF IfSold(Z) = 0 Then
     PRINT USING "| <################### ######## ###,###,###.##|":ItemName$(Z), StockNumber(Z), Price(Z)
     PRINT "|_________________________________________________________|"
     END IF
     NEXT Z
     PRINT "|_________________________________________________________|"
     PRINT
     PRINT "Press any key to continue"
     GET KEY pse
    END SUB

 

Thanks for reading!

Source code for all BASIC programs available at:

https://bitbucket.org/jmercouris/basic

 
