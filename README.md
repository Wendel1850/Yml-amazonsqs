import boto3

sqs = boto3.client('sqs')

# Criar uma fila SQS
sqs.create_queue(QueueName='minha-fila')

# Enviar uma mensagem para a fila
sqs.send_message(QueueUrl='https://sqs.us-east-1.amazonaws.com/123456789012/minha-fila', MessageBody='Olá, mundo!')

# Receber mensagens da fila
response = sqs.receive_message(QueueUrl='https://sqs.us-east-1.amazonaws.com/123456789012/minha-fila')
for message in response['Messages']:
    print(message['Body'])
