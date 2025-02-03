# Martingale
Analysis of Martingale Betting Strategy

The project executes and stores data pertaining to the Martingale betting strategy.

The strategy occurs when the better will have an initial bet size and double the size of the bet after each loss.
After each win, the bet size is reset to the original.
The better has a maximum bank amount which limits how many losses can be had in a row, without completely running out of money.

Examples: W-Win L-Loss
Inital Bet: $1
Maximum Bank: $10
W --> +1
LW --> -1 +2= +1
LLW --> -1 -2 +4= +1
LLLW --> -1 -2 -4 +8 = +1
LLLL --> -1 -2 -4 -8 --> The better cannot afford the 16 dollar bet with the remaining bank = 20-8-4-2-1 = 5

In this program, the martingale continues until the initial bank size doubles or is less than the inital bet amount.
The main metric that I am using to determine the effectiveness of the algorithm is the average scalar effect to inital bank for different values of inital bet size.
For each inital bet size, the simulation is executed for many iterations and the total winnings and total losses are summed and dived byt the number of iterations to result in the average net. (Average net + inital bank)/(initial bank) gives the average scalar effect to inital bank.

Variables:
SEED = 42 is the random seed used for reproducibility
PAY = 1.95 is the pay for betting 1 dollar (win = net +.95, loss = net -1) PAY * BETinit should be an integer value
Ntrials = number of trials to simulate for each BETinit. 100,000 takes est. 1hr @ 16GB RAM. 1500 produces quick results 40 seconds
BANKinit = 200000 the inital bank of the better which limits the total losses
BETinits = [20,200,2000,20000,40000,200000] PAY * BETinit should be an integer value
GOAL = 2 The goal is to "double or nothing" the BANKinit
