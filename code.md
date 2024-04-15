section .text
        global _start           ;must be declared for linker (ld)
                                ;global is used to export the _start label
                                ;This will be the entry point to the program

_start:                         ;tells linker entry point
        mov eax, 7              ;assigns eax register to 7
        mov ebx, eax            ;assigns ebx register to eax, which is 7

loop:                           ;tells loop entry point
        dec ebx                 ;This decrements eax to calculate the factorial
                                ;of 7.
        imul eax, ebx           ;multiplies 7, 6, 5, 4, 3, 2, and 1 to calculate
                                ;the factorial.
        cmp ebx, 1              ;Compares ebx with 1 (If ebx is 1, then eax will
                                ;return the result)
        jg loop                 ;jump to loop if ebx is greater than 1
        jmp exit                ;unconditional jump to exit

exit:                           ;tells exit point
        mov [result], eax       ;returns eax as the result from the calculation
        mov eax, 1              ;set eax register to 1
        int 0x80                ;call kernel (interrupt 0x80)

segment .bss
        result resb 1           ;uninitialized variable result (reserve a byte)
