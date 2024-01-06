# 組語 陣列位置交換12, 34, 56...

INCLUDE Irvine32.inc

.data
	dwarray DWORD 12, 34, 56, 78, 23, 36, 24
	str1 BYTE "The original array :",0dh,0ah,0
	str2 BYTE "after exchange :",0dh,0ah,0
	count EQU (LENGTHOF dwarray)
	rearray DWORD count DUP(0)

.code
main PROC
call crlf
	mov ecx, count
	mov esi, 0
	
L1:
	mov eax, dwarray[esi]
	mov rearray[esi+4], eax
	mov eax, dwarray[esi+4]
	mov rearray[esi], eax
	add esi, 8
	loop L1

	mov edx, OFFSET str1
	call writestring
	mov ecx, count
	mov esi, offset dwarray

L2:
	mov eax, [esi]
	call writedec
	call crlf
	add esi, TYPE dwarray
	loop L2

	mov edx, OFFSET str2
	call writestring
	mov ecx, count
	mov esi, OFFSET rearray

L3:
	mov eax, [esi]
	call writedec
	call crlf
	add esi, TYPE rearray
	loop L3
	exit

main ENDP
END main