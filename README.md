import requests
while (True):
    list1 = []
    response = requests.get("https://bank.gov.ua/")
    response_text = response.text
    response_parse = response_text.split("<span>")
    for element in response_parse:
        if element.startswith('$'):
            for element_2 in element.split("</span>"):
                if element_2.startswith('$') and element_2[1].isdigit():
                    list1.append(element_2)
    print(list1[0])
