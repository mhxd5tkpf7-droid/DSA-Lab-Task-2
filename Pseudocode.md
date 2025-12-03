# Pseudocode for Pharmacy Inventory System

## 1. AddMedicine()

    FUNCTION AddMedicine
        CREATE new node NewMed
        INPUT NewMed.id
        INPUT NewMed.name
        INPUT NewMed.quantity
        INPUT NewMed.price
        SET NewMed.next = head
        SET head = NewMed
        PRINT "Medicine Added"
    END FUNCTION

## 2. Display()

    FUNCTION Display
        IF head == NULL THEN
            PRINT "Inventory Empty"
            RETURN
        END IF

        SET temp = head
        WHILE temp != NULL
            PRINT temp.id, temp.name, temp.quantity, temp.price
            SET temp = temp.next
        END WHILE
    END FUNCTION

## 3. SearchMedicine()

    FUNCTION SearchMedicine
        INPUT id
        SET temp = head

        WHILE temp != NULL
            IF temp.id == id THEN
                PRINT "Found", temp.name, temp.quantity, temp.price
                RETURN
            END IF
            SET temp = temp.next
        END WHILE

        PRINT "Medicine Not Found"
    END FUNCTION

## 4. DeleteMedicine()

    FUNCTION DeleteMedicine
        INPUT id
        SET temp = head
        SET prev = NULL

        WHILE temp != NULL
            IF temp.id == id THEN
                IF prev == NULL THEN
                    SET head = temp.next
                ELSE
                    SET prev.next = temp.next
                END IF

                DELETE temp
                PRINT "Medicine Deleted"
                RETURN
            END IF

            SET prev = temp
            SET temp = temp.next
        END WHILE

        PRINT "Medicine Not Found"
    END FUNCTION

## 5. MainMenu()

    FUNCTION MainMenu
        DO
            PRINT Menu Options
            INPUT choice

            SWITCH choice
                CASE 1: CALL AddMedicine
                CASE 2: CALL Display
                CASE 3: CALL SearchMedicine
                CASE 4: CALL DeleteMedicine
                CASE 5: PRINT "Exit"
                DEFAULT: PRINT "Invalid Choice"
            END SWITCH
        WHILE choice != 5
    END FUNCTION
