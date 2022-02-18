#!/bin/python3
import re 
import csv

filenames = (r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\sw1_dhcp_snooping.txt", r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\sw2_dhcp_snooping.txt", r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\sw3_dhcp_snooping.txt")
def write_dhcp_snooping_to_csv(filenames, output):
    regex = '(\S+)\s+(\S+)\s+\d+\s+\S+\s+(\S+)\s+(\S+)'
    result = []
    with open (output, "a", newline='') as f:
        writer = csv.writer(f, delimiter=';', quoting=csv.QUOTE_MINIMAL)
        writer.writerow(["switch", "mac", "ip", "vlan", "interface"])
        for file in filenames:
            switch = re.search('(\w+\d+)_', file).group(1)
            with open (file) as a:
                for line in a:
                    match = re.finditer(regex, line)
                    for m in match:
                        result.append(m.groups())
                        writer.writerow((switch,) + m.groups())
                print(a)
        print(result)
        print(switch)
# for value in result:
#writer.writerow(value)
write_dhcp_snooping_to_csv(filenames, r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\output.csv")
def vprn(filename):
    regex = 'ip vrf (\S+)'
    result = []
    with open (output, "w", newline='') as f:
        writer = csv.writer(f, delimiter=';', quoting=csv.QUOTE_MINIMAL)
    with open (filename) as a:
        for line in a:
            match = re.finditer(regex, line)
            for m in match:
                result.append(m.groups())
import re
import csv

def get_ip_from_cfg(confile, vrftable):
    regex = ('ip vrf (\S+)\n'
    '(.*\n*)'
    ' rd (\S+)\n'
    ' route-target export (\S+)\n'
    ' route-target import (\S+)\n'
    )
    result = []
    vrf_result = []
    with open (vrftable,  "w") as f:
    	writer = csv.writer(f)
    	writer.writerow(["name", "description", "rd", "rt",  "rt"])
    with open(confile) as a:
    	match = re.finditer(regex, a.read())
    with open (vrftable,  "w", newline = '') as f:
    	writer = csv.writer(f, delimiter=';', quoting=csv.QUOTE_MINIMAL)
    	writer.writerow(["HOST A", "Lo0_Nokia", "name", "description", "rd", "rt",  "rt"])
    	if match:
    		for m in match:
    			#print(match)
    			ip = m.group(1)
    			if "description" in m.group(2):
    				mask = re.search('description (.*)\n', m.group(2)).group(1)
    			elif not "description" in m.group(2):mask = m.group(1)
    			print(ip)
    			print(mask)
    			state = m.group(3)
    			print(state)
    			state1 = m.group(4)
    			print(state1)
    			result.append([ip + ',' + mask])
    			vrf_result.append(result)
    			#result = {'ip', 'mask'}
    			writer.writerow([" "] + [" "] + [m.group(1)] + [mask] + [m.group(3)] + [m.group(4)])
                        #	print(line)
    	print(vrf_result)
    #	writer.writerow(vrf_result)
    	return(result)
    	return(ip) 
		
def ip_forwarding_vrf(filename, table):
	get_ip_from_cfg(filename, table)
#	with open(filename) as a:
	#	for ip in get_ip_from_cfg(filename, table):
#	regex = (' ip vrf forwarding (\S+)\n')
    #rresult = []
	#match1 = re.finditer(regex, a.read())
		 #   if  match1:
		    #	for q in match1:
			    #    rresult.append(q.groups())
	#	print(rresult)

ip_forwarding_vrf(r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\cisco86.txt", r"C:\Users\e_yarotskov\AppData\Local\Programs\Python\Python38\Scripts\conf_parse_cisco\cisco\vrf.csv")
