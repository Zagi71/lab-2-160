# lab-2-160
#Sequence Cleanup 
'''
Read a DNA string from user input and return a collapsed substring of embedded Ns to: {count}.

Example: 
 input: AaNNNNNNGTC
output: AA{6}GTC

Any lower case letters are converted to uppercase
'''

class DNAstring (str):
    def length (self):
        return (length(self))
    
    def purify(self):
        ''' Return an upcased version of the string, collapsing a single run of Ns.
            There is at most one continous Block of Ns in DNA sequence.
            Therefore, if the number of the Ns is not zero, then all the Ns are consective.
        '''
        #This line of code willconvert the DNA sequence to UPPERCASE.
        self=self.upper()
        #This will create a variable count that store the Number of times N occur
        cont=self.count('N')
        #If there is a Block of Ns we will Replace it with {Length of Ns}, The code in if block just Do that
        if cont!=0:
            #We will find the starting adress of Ns, Block,
            start=self.index('N')
            #This is a temporary string that Store Number of Ns inside Curly Brackets i.e {5}
            replace='{'+str(cont)+'}'
            #This Line of code will Replace the Ns with empty space mean it just delete all Ns.
            self=self.replace('N','')
            #This code Add the replace string where the block of Ns was present.
            self=self[0:start]+replace+self[start:len(self)]
        #return Upper() cased string with collapsing of Ns if any,
        return self

    
def main():
    ''' Get user DNA data and clean it up.'''
    data = input('DNA data?')
    thisDNA = DNAstring (data)
    pureData = thisDNA.purify()
    print (pureData)
    
main()
