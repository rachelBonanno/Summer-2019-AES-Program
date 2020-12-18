theme: jekyll-theme-hacker

#! /usr/bin/python

import binascii
import time
import base64

def cconvertToBinary(message):
    string = message
    return(bin(int(binascii.hexlify(string), 16)))

def keybyteSub(message):
	byteAr = [[0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0]]	
	i = 0
	j = 0
	k = 0
	while i < 4:
		while j < 4:
			byteAr[i][j] = message[k]
			#print(byteAr)
			k = k + 1
			j = j + 1
		i = i + 1
		j = 0
	return(byteAr)

def keymatrixSub(beret):
	encrypte_mat_1 = [[0,0,0,0],
					 [0,0,0,0],
			 		[0,0,0,0],
			 		[0,0,0,0]]	
	i = 0
	j = 0
	k = 0
	while i < 4:
		while j < 4:
			hexvar = ord(beret[i][j])
			#print(hexvar)
			hafhexfir = (hexvar & 0xF0) >> 4
			#print(hafhexfir)
			hafhexsec = hexvar & 0x0F
			#print(hafhexsec)
			encrypte_mat_1[i][j] += sbox[hafhexsec][hafhexfir]
			k = k + 1
			j = j + 1
			#print(encrypte_mat_1)
		i = i + 1
		j = 0
		#print(hexvar)
	return(encrypte_mat_1)


# MESSAGE DEF:

def formatMessage(message):
	prepedmessa = ""
	#print(message)
	for ch in message:
		if ord(ch)!= 32:
			prepedmessa = prepedmessa + ch
			#print(prepedmessa)
	pmessalength = len(prepedmessa)
	#print(pmessalength)
	while pmessalength % 16 != 0:
		prepedmessa = prepedmessa + "x"
		pmessalength = pmessalength + 1
		#print(prepedmessa)
		#print(pmessalength)
	return(prepedmessa)



def byteSub(message):
	byteAr = [[0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0]]	
	i = 0
	j = 0
	k = 0
	while i < 4:
		while j < 4:
			byteAr[i][j] = message[k]
			#print(byteAr)
			k = k + 1
			j = j + 1
		i = i + 1
		j = 0
	return(byteAr)

def matrixSub(beret):
	encrypte_mat_1 = [[0,0,0,0],
					 [0,0,0,0],
			 		[0,0,0,0],
			 		[0,0,0,0]]	
	i = 0
	j = 0
	k = 0
	while i < 4:
		while j < 4:
			hexvar = ord(beret[i][j])
			#print(hexvar)
			hafhexfir = (hexvar & 0xF0) >> 4
			#print(hafhexfir)
			hafhexsec = hexvar & 0x0F
			#print(hafhexsec)
			encrypte_mat_1[i][j] += sbox[hafhexsec][hafhexfir]
			k = k + 1
			j = j + 1
			#print(encrypte_mat_1)
		i = i + 1
		j = 0
		#print(hexvar)
	return(encrypte_mat_1)

def shiftRow(shray):
	# 1st row not altered
	# 2nd row shifts left 1
	# 3rd row shifts left 2
	# 4th row shifts left 3
	rowShits = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]	
	i = 0
	j = 0
	while i < 4:
		while j < 4:
			if i == 0:
				rowShits[i][j] = shray[i][j]
			elif (i == 1):
				if (j == 3):
					rowShits[i][j] += shray[i][0]
				else:
					rowShits[i][j] += shray[i][j + 1]
			
			elif (i == 2):
				if (j == 3):
					rowShits[i][j] += shray[i][1]
				elif (j == 2):
					rowShits[i][j] += shray[i][0]
				else:
					rowShits[i][j] += shray[i][j + 2]
			else:
				if (j == 3):
					rowShits[i][j] += shray[i][0]
				elif (j == 2):
					rowShits[i][j] += shray[i][3]
				elif (j == 1):
					rowShits[i][j] += shray[i][2]
				else:
					rowShits[i][j] += shray[i][1]
			j = j + 1
		i = i + 1
		j = 0
	return(rowShits)

def mixColumn(shicolm):
	colShifs = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]	
	i = 0
	j = 0
	while i < 4:
		while j < 4:
			if j == 0:
				colShifs[i][j] = shicolm[i][j]
			elif (j == 1):
				if (i == 3):
					colShifs[i][j] += shicolm[0][j]
				else:
					colShifs[i][j] += shicolm[i + 1][j]
			elif (j == 2):
				if (i == 3):
					colShifs[i][j] += shicolm[1][j]
				elif (i == 2):
					colShifs[i][j] += shicolm[0][j]
				else:
					colShifs[i][j] += shicolm[i + 2][j]
			else:
				if (i == 3):
					colShifs[i][j] += shicolm[0][j]
				elif (i == 2):
					colShifs[i][j] += shicolm[3][j]
				elif (i == 1):
					colShifs[i][j] += shicolm[2][j]
				else:
					colShifs[i][j] += shicolm[1][j]
			j = j + 1
		i = i + 1
		j = 0
	return(colShifs)



# CYPHER TEXT (XOR):

def creatingCypherTEXT(messa, key):
	cipherText = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]	
	i = 0
	j = 0
	while i < 4:
		while j < 4:
			cipherText[i][j] += messa[i][j] ^ key[i][j]
			j = j + 1
		i = i + 1
		j = 0
	return(cipherText)

def ecryptFMessage(message):
	prepedmessa = ""

	i = 0
	j = 0
	while i < 4:
		while j < 4:
			prepedmessa += chr(message[i][j])
			#print(prepedmessa)
			j = j + 1
		i = i + 1
		j = 0
	return(prepedmessa)

# DECRYPTION:

def cypherTOAR(message):
	Ar = [[0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0],
			 [0,0,0,0]]	
	print(len(message))
	print(message)
	i = 0
	j = 0
	k = 0
	while i < 4:
		while j < 4:
			Ar[i][j] = message[k]
			#print(byteAr)
			k = k + 1
			j = j + 1
		i = i + 1
		j = 0
	return(Ar)


def decryptCypherTEXT(cypher, key):

	print(cypher)
	cypherAR = cypherTOAR(cypher)

	messa = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]
	i = 0
	j = 0
	#rint("lenght of cypher")
	while i < 4:
		while j < 4:
			messa[i][j] += ord(cypherAR[i][j]) ^ key[i][j]

			j = j + 1
		i = i + 1
		j = 0
	return(messa)

def reversemixColumn(shicolm):
	colShifs = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]	
	i = 0
	j = 0
	while i < 4:
		while j < 4:
			if j == 0:
				colShifs[i][j] = shicolm[i][j]
			elif (j == 1):
				if (i == 0):
					colShifs[i][j] += shicolm[3][j]
				else:
					colShifs[i][j] += shicolm[i - 1][j]
			elif (j == 2):
				if (i == 1):
					colShifs[i][j] += shicolm[3][j]
				elif (i == 0):
					colShifs[i][j] += shicolm[2][j]
				else:
					colShifs[i][j] += shicolm[i - 2][j]
			else:
				if (i == 0):
					colShifs[i][j] += shicolm[3][j]
				elif (i == 3):
					colShifs[i][j] += shicolm[2][j]
				elif (i == 2):
					colShifs[i][j] += shicolm[1][j]
				else:
					colShifs[i][j] += shicolm[0][j]
			j = j + 1
		i = i + 1
		j = 0
	return(colShifs)

def decrypt(decryptshray):
	# 1st row not altered
	# 2nd row shifts left 1
	# 3rd row shifts left 2
	# 4th row shifts left 3
	rowShits = [[0,0,0,0],
				[0,0,0,0],
			 	[0,0,0,0],
			 	[0,0,0,0]]	
	i = 0
	j = 0
	while i < 4:
		while j < 4:
			if i == 0:
				rowShits[i][j] = decryptshray[i][j]
			elif (i == 1):
				if (j == 0):
					rowShits[i][j] += decryptshray[i][3]
				else:
					rowShits[i][j] += decryptshray[i][j - 1]
			
			elif (i == 2):
				if (j == 0):
					rowShits[i][j] += decryptshray[i][2]
				elif (j == 1):
					rowShits[i][j] += decryptshray[i][3]
				else:
					rowShits[i][j] += decryptshray[i][j - 2]
			else:
				if (j == 1):
					rowShits[i][j] += decryptshray[i][0]
				elif (j == 2):
					rowShits[i][j] += decryptshray[i][1]
				elif (j == 3):
					rowShits[i][j] += decryptshray[i][2]
				else:
					rowShits[i][j] += decryptshray[i][3]
			j = j + 1
		i = i + 1
		j = 0
	return(rowShits)

def decmatrixSub(deret):
	plaintext = [[0,0,0,0],
					 [0,0,0,0],
			 		[0,0,0,0],
			 		[0,0,0,0]]	
	i = 0
	j = 0
	x = 0
	y = 0
	while i < 4:
		while j < 4:
			hexcord = deret[i][j]
			while y < 16:
				while x < 16:
					if sbox[x][y] == hexcord:
						plaintext[i][j] = (y << 4)| x			
						break
					x = x + 1
				y = y + 1
				x = 0
			j = j + 1
			y = 0
		i = i + 1
		j = 0
		#y = 0
		#x = 0

					
	return plaintext

def decryptFMessage(message):
	prepedmessa = ""

	i = 0
	j = 0
	while i < 4:
		while j < 4:
			prepedmessa += chr(message[i][j])
			#print(prepedmessa)
			j = j + 1
		i = i + 1
		j = 0
	return(prepedmessa)


def encrypts(messa, hexkeyToBox):
	#formatted message
	formattedMessage = formatMessage(messa)
	print("formating message:")
	print(formattedMessage)

	#byte array
	byteSubAR = byteSub(formattedMessage)
	print("message made into byte array:")
	print(byteSubAR)

	#byte sub array
	hexWorkToBox = matrixSub(byteSubAR)
	print("message converted to hex and put into the s-box:")
	print(hexWorkToBox)

	#shifted row
	rowShiffting = shiftRow(hexWorkToBox)
	print("rows of array of the message shift:")
	print(rowShiffting)

	#column shift
	shitingCol = mixColumn(rowShiffting)
	print("columbs of the array message are mixed:")
	print(shitingCol)

	# the cypher text using XOR
	theCYPHER = creatingCypherTEXT(shitingCol, hexkeyToBox)
	print("the array of the message gets XOR:")
	print(theCYPHER)

	plaitext = ecryptFMessage(theCYPHER)
	return(plaitext)


def decrypts(theCYPHER, hexkeyToBox):
	# decrypting the cyoher using the key and cypher text
	#print(theCYPHER)
	decrypttheCYPHER = decryptCypherTEXT(theCYPHER, hexkeyToBox)
	print("the encrypted message gets XOR and starts to be decrypted:")
	print(decrypttheCYPHER)

	# reverse shift the columbs
	decryptMixCol = reversemixColumn(decrypttheCYPHER)
	print("the encrypted array has the colums mixed back to decrypt the message:")
	print(decryptMixCol)

	# reverse shirt of the rows
	decryptrow = decrypt(decryptMixCol)
	print("the encrypted array has its rows shifted to decrypt the message:")
	print(decryptrow)

	# revers byte subarray
	subArrayRev = decmatrixSub(decryptrow)
	print("the encrypted message is made into letters and kept in an array:")
	print(subArrayRev)

	#convert back to ascii
	messageBack = decryptFMessage(subArrayRev)
	return(messageBack)



# CALLLING FUNCTIONS:

sbox = [[0x63, 0x7c, 0x77, 0x7b, 0xf2, 0x6b, 0x6f, 0xc5, 0x30, 0x01, 0x67, 0x2b, 0xfe, 0xd7, 0xab, 0x76],
        [0xca, 0x82, 0xc9, 0x7d, 0xfa, 0x59, 0x47, 0xf0, 0xad, 0xd4, 0xa2, 0xaf, 0x9c, 0xa4, 0x72, 0xc0],
        [0xb7, 0xfd, 0x93, 0x26, 0x36, 0x3f, 0xf7, 0xcc, 0x34, 0xa5, 0xe5, 0xf1, 0x71, 0xd8, 0x31, 0x15],
        [0x04, 0xc7, 0x23, 0xc3, 0x18, 0x96, 0x05, 0x9a, 0x07, 0x12, 0x80, 0xe2, 0xeb, 0x27, 0xb2, 0x75],
        [0x09, 0x83, 0x2c, 0x1a, 0x1b, 0x6e, 0x5a, 0xa0, 0x52, 0x3b, 0xd6, 0xb3, 0x29, 0xe3, 0x2f, 0x84],
        [0x53, 0xd1, 0x00, 0xed, 0x20, 0xfc, 0xb1, 0x5b, 0x6a, 0xcb, 0xbe, 0x39, 0x4a, 0x4c, 0x58, 0xcf],
        [0xd0, 0xef, 0xaa, 0xfb, 0x43, 0x4d, 0x33, 0x85, 0x45, 0xf9, 0x02, 0x7f, 0x50, 0x3c, 0x9f, 0xa8],
        [0x51, 0xa3, 0x40, 0x8f, 0x92, 0x9d, 0x38, 0xf5, 0xbc, 0xb6, 0xda, 0x21, 0x10, 0xff, 0xf3, 0xd2],
        [0xcd, 0x0c, 0x13, 0xec, 0x5f, 0x97, 0x44, 0x17, 0xc4, 0xa7, 0x7e, 0x3d, 0x64, 0x5d, 0x19, 0x73],
        [0x60, 0x81, 0x4f, 0xdc, 0x22, 0x2a, 0x90, 0x88, 0x46, 0xee, 0xb8, 0x14, 0xde, 0x5e, 0x0b, 0xdb],
        [0xe0, 0x32, 0x3a, 0x0a, 0x49, 0x06, 0x24, 0x5c, 0xc2, 0xd3, 0xac, 0x62, 0x91, 0x95, 0xe4, 0x79],
        [0xe7, 0xc8, 0x37, 0x6d, 0x8d, 0xd5, 0x4e, 0xa9, 0x6c, 0x56, 0xf4, 0xea, 0x65, 0x7a, 0xae, 0x08],
        [0xba, 0x78, 0x25, 0x2e, 0x1c, 0xa6, 0xb4, 0xc6, 0xe8, 0xdd, 0x74, 0x1f, 0x4b, 0xbd, 0x8b, 0x8a],
        [0x70, 0x3e, 0xb5, 0x66, 0x48, 0x03, 0xf6, 0x0e, 0x61, 0x35, 0x57, 0xb9, 0x86, 0xc1, 0x1d, 0x9e],
        [0xe1, 0xf8, 0x98, 0x11, 0x69, 0xd9, 0x8e, 0x94, 0x9b, 0x1e, 0x87, 0xe9, 0xce, 0x55, 0x28, 0xdf],
        [0x8c, 0xa1, 0x89, 0x0d, 0xbf, 0xe6, 0x42, 0x68, 0x41, 0x99, 0x2d, 0x0f, 0xb0, 0x54, 0xbb, 0x16]]

# what the key is
print("key:")
key = "go"
print(key)

keyl = bin(int(binascii.hexlify(key), 16))
#print(cconvertToBinary(key))

# the length of the key
keylength = len(keyl)-1
#print(keylength)

# adding Xs to the end of the key to make the length divisible by 16
# formating key
while keylength != 128 and keylength != 192 and keylength != 256 and keylength < 258:
    key = key + "x"
    keylength = keylength + 8
    #print(key)
    #print(keylength)

bytekeySubAR = keybyteSub(key)

#byte sub array
fkey = keymatrixSub(bytekeySubAR)
print("formated key:")
print(fkey)

#####################################################

#plaintext message
print("message:")
messag = "ttest"
print(messag)

# if message is longer then 16 
# repeate untill % = 0
messag = formatMessage(messag)
ciphertext = ""
#print(messag)
while len(messag) >= 16:
	toBeEncrypt = ""
	for i in range(len(messag)):
		#print(i)
		#print(toBeEncrypt)
		#print(messag)
		toBeEncrypt += messag[i]
	messag = messag[16:]
	ciphertext += encrypts(toBeEncrypt, fkey)
print("ciphertext:")
print(ciphertext)


print("length of ciphertext:")
print(len(ciphertext))

plaintext =""
messtext = decrypts(ciphertext, fkey)
#print(messtext)
if len(ciphertext) <= 16:
	for i in range(len(ciphertext)):
		#print(i)
		print("ciphertext:")
		print(messtext)
		#print(messag)
		messtext += ciphertext[i]
	plaintext += decrypts(ciphertext, fkey)

	#ciphertext = ciphertext[16:]
	#plaintext += decrypts(ciphertext, fkey)

else:
	while len(ciphertext) > 16:
		messtext = ""
		for i in range(len(ciphertext)):
			#print(i)
			#print("ciphertext:")
			#print(messtext)
			#print(messag)
			messtext += ciphertext[i]
		plaintext += decrypts(ciphertext, fkey)

		ciphertext = ciphertext[16:]
		plaintext += decrypts(ciphertext, fkey)

	
print("decrypted message:")
print(plaintext)
