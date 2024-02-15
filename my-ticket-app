import React, { useState } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import { Container, Row, Col, ListGroup, Form, Button } from 'react-bootstrap';

const App = () => {
  const [tickets, setTickets] = useState([
    { id: 1, description: 'Issue with printer', contactNumber: '123-456-7890', priority: 'High', date: '2022-01-01', notes: '' },
    { id: 2, description: 'Issue with internet', contactNumber: '987-654-3210', priority: 'Low', date: '2022-01-02', notes: '' },
  ]);

  const addTicket = (ticket) => {
    setTickets([...tickets, ticket]);
  };

  const updateTicket = (id, updatedTicket) => {
    setTickets(tickets.map(ticket => (ticket.id === id ? updatedTicket : ticket)));
  };

  return (
    <Router>
      <Container>
        <Row>
          <Col md={4}>
            <ListGroup>
              {tickets.map(ticket => (
                <ListGroup.Item action href={`/tickets/${ticket.id}`}>
                  {ticket.description}
                </ListGroup.Item>
              ))}
              <Button block onClick={() => addTicket({ id: tickets.length + 1, description: '', contactNumber: '', priority: '', date: '', notes: '' })}>
                Add Ticket
              </Button>
            </ListGroup>
          </Col>
          <Col md={8}>
            <Switch>
              <Route path="/tickets/:id" render={({ match }) => {
                const ticket = tickets.find(ticket => ticket.id === parseInt(match.params.id));
                return (
                  <Form>
                    <Form.Group controlId="description">
                      <Form.Label>Description</Form.Label>
                      <Form.Control type="text" placeholder="Enter description" value={ticket.description} onChange={e => updateTicket(ticket.id, { ...ticket, description: e.target.value })} />
                    </Form.Group>
                    <Form.Group controlId="contactNumber">
                      <Form.Label>Contact Number</Form.Label>
                      <Form.Control type="text" placeholder="Enter contact number" value={ticket.contactNumber} onChange={e => updateTicket(ticket.id, { ...ticket, contactNumber: e.target.value })} />
                    </Form.Group>
                    <Form.Group controlId="priority">
                      <Form.Label>Priority</Form.Label>
                      <Form.Control as="select" value={ticket.priority} onChange={e => updateTicket(ticket.id, { ...ticket, priority: e.target.value })}>
                        <option>High</option>
                        <option>Medium</option>
                        <option>Low</option>
                      </Form.Control>
                    </Form.Group>
                    <Form.Group controlId="date">
                      <Form.Label>Date</Form.Label>
                      <Form.Control type="date" value={ticket.date} onChange={e => updateTicket(ticket.id, { ...ticket, date: e.target.value })} />
                    </Form.Group>
                    <Form.Group controlId="notes">
                      <Form.Label>Notes</Form.Label>
                      <Form.Control as="textarea" rows={3} value={ticket.notes} onChange={e => updateTicket(ticket.id, { ...ticket, notes: e.target.value })} />
                    </Form.Group>
                  </Form>
                );
              }} />
            </Switch>
          </Col>
        </Row>
      </Container>
    </Router>
  );
};

export default App;
