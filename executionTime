#!/usr/bin/python

# "executionTime" is under the MIT License
# Copyright (c) 2013 Jean-Etienne Morlighem <jem.nvnt@gmail.com>
# https://github.com/jem-gh/tools



import time

def executionTime(list_fn, list_param=None, num_exec=10):
    """ calculate the execution time of a function or of comparable functions 
        provided in a list (list_fn), with their parameter or list of parameters 
        (list_param), by executing each function x number of times (num_exec) """
    
    if num_exec < 1:
        print "executionTime: number of executions (num_exec) should be >= 1"
        return False
    
    # if executionTime is called with one function and/or one parameter which 
    # are not in list(s)/tuple(s)
    if not isinstance(list_fn, (list, tuple)):
        list_fn = [list_fn]
    if list_param and not isinstance(list_param, (list, tuple)):
        list_param = [list_param]
    
    # start printing result table
    WIDTH, PRECISION = 12, 3    # globals for printing result table
    print "executionTime: running time (in sec) for {0} execution(s)".format(num_exec)
    print "|{0:^{w}}|{1:^{w}}|{2:^{w}}|{3:^{w}}|".format(
                      "min", "max", "mean", "total", w=WIDTH)
    
    for fn in list_fn:
        times = []
        
        for i in range(num_exec):
            t0 = time.time()
            try:
                fn() if not list_param else fn(*list_param)
            except TypeError:
                print "executionTime: function to be tested not valid"
                return False
            times.append(time.time() - t0)
        
        t_min  = min(times)
        t_max  = max(times)
        t_tot  = sum(times)
        t_mean = t_tot / num_exec
        
        # print results for current function under test
        print "|{0:^{w}.{p}g}|{1:^{w}.{p}g}|{2:^{w}.{p}g}|{3:^{w}.{p}g}| {4}".format(
                        t_min, t_max, t_mean, t_tot, fn.__name__, w=WIDTH, p=PRECISION)






#################### EXAMPLES ####################

def factorial_of_50a():
    return reduce(lambda x, y: x*y, [n for n in range(1,51)])

def factorial_of_50b():
    res = 1
    for n in range(1,51):
        res *= n
    return res

#executionTime(factorial_of_50a)
#executionTime(factorial_of_50a, num_exec=100)
#executionTime((factorial_of_50a, factorial_of_50b))
#executionTime((factorial_of_50a, factorial_of_50b), num_exec=5000)


def countInString_1(string):
    toCount = {"1":0, "2":0, "3":0, "4":0}
    for i in string:
        toCount[i] += 1

def countInString_2(string):
    n1 = string.count("1")
    n2 = string.count("2")
    n3 = string.count("3")
    n4 = string.count("4")

s = "123134241231243421313212324241323134441"

#executionTime((countInString_1, countInString_2), s)
#executionTime((countInString_1, countInString_2), s, 10000)


def ex_multiply1(x,y,z):
    return x*y*z

def ex_multiply2(x,y,z):
    return int((x**2)**.5 * (y**2)**.5 * (z**2)**.5)

#executionTime(ex_multiply1, [2, 4, 6])
#executionTime(ex_multiply1, (2, 4, 6), 100)
#executionTime([ex_multiply1, ex_multiply2], [5, 8, 19])
#executionTime((ex_multiply1, ex_multiply2), (5, 8, 19), 100)

